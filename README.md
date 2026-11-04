# Strapi application stack for Kubernetes on Wodby

Deploy Strapi applications on Kubernetes with Wodby.

This repository defines the Wodby stack manifests and default service
composition for Strapi.

<!-- wodby:generated:start -->

## Stack contract

- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Start from a boilerplate

Use one of the compatible boilerplates exposed by this stack's services to
start with Wodby CI build configuration:

- [Strapi Boilerplate](https://github.com/wodby/strapi-boilerplate)

## Service definitions

- [Node.js (Strapi) service](https://github.com/wodby/service-strapi)
- [PostgreSQL service](https://github.com/wodby/service-postgres)
- [Mailpit service](https://github.com/wodby/service-mailpit)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Node.js<br>`strapi` | required; enabled by default; volumes: `uploads` 10 GB; links: `db` → `postgres`, `sendmail` → `mailpit` |
| PostgreSQL<br>`postgres` | required; enabled by default; volumes: `data` 10 GB |
| Mailpit<br>`mailpit` | optional; disabled by default |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Deploy this stack

Start from [Strapi Boilerplate](https://github.com/wodby/strapi-boilerplate), or connect your own compatible
source repository.

Strapi stores its content in PostgreSQL and uploaded media on the Node.js
service's `uploads` volume. Enable Mailpit to catch the emails Strapi sends,
such as password resets, or OpenSMTPD to deliver them.

Review service versions, storage, links, and optional components when creating
the application. The same stack can be reused across development, staging, and
production environments.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
