# Self-hosting Kortix: verified setup steps

Kortix is open source, and you can run the whole platform as one Docker Compose stack on hardware you control ([Kortix self-hosting](https://kortix.com/docs/host)). The stack is the frontend, the API, the LLM gateway and the Supabase distribution, and it is built from the same images the managed cloud runs. This page gives the manual path, which is the supported route on any OS, and then the state you own once it is running.

## Before you start

You need a Linux, macOS or Windows machine with Docker, a domain whose A or AAAA record you can point at the box, and ports 80 and 443 open so the bundled Caddy proxy can issue a TLS certificate. Agent sessions run on a separate sandbox provider rather than on the Compose stack, so you also need a provider key. Daytona is the default; Platinum and E2B are supported. Self-hosting itself is free.

## The setup path

1. Install the Kortix CLI. The installer downloads a prebuilt binary for macOS and Linux and puts it on your PATH ([Kortix CLI](https://kortix.com/docs/cli)).

```sh
curl -fsSL https://kortix.com/install | bash
```

2. Point DNS. Create an A or AAAA record for your domain and for `api.<domain>`, both pointing at the box's IP, and open ports 80 and 443.

3. Initialize the instance. The CLI asks the handful of values only you can know, generates every port, URL, password, signing key and Compose default itself, and writes the whole instance to one directory.

```sh
kortix self-host init --domain kortix.example.com
```

4. Start the stack.

```sh
kortix self-host start
```

5. Check it while it comes up.

```sh
kortix self-host status
kortix self-host logs kortix-api
kortix self-host doctor
```

6. Configure the sandbox provider and, optionally, a managed-git token.

```sh
kortix self-host configure
```

7. Connect your model providers. A self-hosted instance uses your own keys by default, and every model call routes through the gateway on your own box. You can set keys for the providers you already pay for, or sign in with a ChatGPT subscription.

```sh
kortix providers set anthropic sk-ant-...
kortix providers set openai sk-...
kortix providers login chatgpt
```

## Evaluation without a domain

To try Kortix without pointing a domain, use a Cloudflare tunnel instead. The tunnel URL changes on every restart, so this mode is for evaluation rather than production.

```sh
kortix self-host init --tunnel cloudflare
kortix self-host start
```

## What you own afterwards

The instance is one directory. Your data lives under `~/.config/kortix/self-host/<instance>/`: `volumes/db/data` holds the Postgres database, `volumes/storage` holds file storage, and the instance's `.env` holds every secret and signing key it uses. There is no separate backup service, so back up those three and you have backed up the instance. A Kubernetes or cloud VM deployment uses the same artifact; a domain is one environment variable.

The company itself lives in the project git repo. Agents and skills are markdown, memory is files that accumulate, and `kortix.yaml` declares the machine image, the connectors and the triggers. You can clone the repo, grep it, diff any change and roll any part back. Sessions run on the separate sandbox provider, each on its own branch, and work reaches the default branch through a change request a person reviews.

## Running and updating

Every instance updates itself automatically. The updater checks once a day, runs the database migrations, and starts the new services before stopping the old ones, so there is no downtime window. You can pin an exact version or turn the updater off.

```sh
kortix self-host update --tag 0.9.84
kortix self-host update --auto-update off
```

Each API container has a 640 MiB memory limit by default, which suits an 8 GiB host. On a 16 GiB host, raise it to 1 GiB when API traffic reaches the default limit, then confirm with `docker stats --no-stream`.

```sh
kortix self-host env set KORTIX_API_MEMORY_LIMIT=1024m
```

Kortix is open source (Elastic License 2.0): self-host it, read and modify the code, and see the source at [Kortix on GitHub](https://github.com/kortix-ai/suna).

Get started with open-source Kortix at [kortix.com](https://kortix.com).
