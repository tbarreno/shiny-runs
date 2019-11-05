# Shiny-Runs

A Node.js remote execution solution (*Proof-of-Concept*).

This project contains the ideas and design for a discarded solution for
IT automation (remote scripting execution).

## Introduction

As part of a DevOps team for years, I've notice that there's a frequent need
for some kind of automation self-service, mainly running some privieged IT
operation or script on a remote server.

The background is that experienced technical engineers build scripts for many
tasks that can be delegated to operators or directly to users while keeping
execution authorization and auditory. This frees engineers from running the
operations and reporting the results.

A good approach must be able to offer "*level 3*" automation solution
with features like:

- **Configuration management** for infrastructure and services (i.e.
hostnames/ports, paths, default values, etc.)
- A user **self-service front-end** where they can:
  - See the offered catalog (customized for the user/group/role)
  - Follow the request's status and see the results and logs
- A developer **front-end** or **ID** where they can:
  - Develop and test new scripts
  - Configure the script execution workflow (chain of scripts)
  - Setup the catalog, offering the executions to the users/groups roles
- An **administrative console** for user/group/role management.
- A **workflow** engine for chaining executions and controlling exceptions
and errors.
- Some kind of scalable **remote agents** for the scripting execution.

## First approach

A tentative overall design picture would roughly be like that:

![Overview design](images/overview.png "Overview design")

The front-end user interface must support users with different
roles or profiles for the four main modules (execution, development,
configuration and general management). It could be a *Rich Internet
Application* or a desktop/mobile application.

The central block comprises all the UI services (mostly for CRUD operations),
the backend access and two execution components: one providing the workflow
engine and another one for the remote agent communication.

The remote agents are instances of a scalable component that pulls from an
execution pool and returns the resunting logs and status.

We will also need some log storage and a source code repository for the
scripts.

P.S. The project name ('shiny-runs') was proposed by the GitHub's random
project generator; it's not planned.
