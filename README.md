# Lab 2 — Backend - run locally, fix a bug, deploy on a server

<h2>Table of contents</h2>

- [Lab story](#lab-story)
- [Learning advice](#learning-advice)
- [Learning outcomes](#learning-outcomes)
- [Tasks](#tasks)
  - [Prerequisites](#prerequisites)
  - [Required](#required)
  - [Optional](#optional)

## Lab story

You were hired by a company that develops a novel e-learning system.

The system recommends educational resources to students.

You joined a [back end](https://roadmap.sh/backend) team working on a web server for the **Course Materials Service**.

The web server is implemented using the [`FastAPI`](https://fastapi.tiangolo.com/) framework in [`Python`](https://www.python.org/).

Currently, it serves courses-related items (courses, labs, tasks, steps).

For simplicity, the web server uses data stored is [`JSON`](https://en.wikipedia.org/wiki/JSON) files (`JSON resources`) in [`src/app/data/course_items.json`](./src/app/data/course_items.json).

A senior engineer explains your first assignment:

> 1. Run our web server on your machine.
> 2. Verify that it’s working: query the `/status` endpoint.
> 3. Investigate and fix a bug in the `/items` endpoint.
> 4. Deploy the web server to a remote `Linux` [virtual machine](./lab/appendix/vm.md).

> [!IMPORTANT]
> Communicate through issues and PRs and deliver a working deployment.

## Learning advice

Read the tasks and complete them by yourself.

When stuck or not sure, ask an LLM:

> Give me directions on how to solve this task. I want to maximize learning.

> Why is this task important? What exactly do I need to do?

Provide enough context by giving it the whole file, not one or two lines.

Remember: Use the LLM to enhance your understanding, not replace it.

Evaluate LLM answers critically, and verify them against credible sources such as official documentation, course materials, and what you observe in reality.

## Learning outcomes

By the end of this lab, you should be able to:

- Follow the [`Git workflow`](./lab/tasks/git-workflow.md).
- Check your work against specified acceptance criteria.
- Explore the code of an existing web server written in `Python`.
- Run the web server on your computer.
- Query the web server.
- Inspect the responses of the web server.
- Test the web server.
- Identify a bug (problem) in the web server.
- Document the bug using a `GitHub` issue.
- Submit a fix of the bug as a PR.
- Deploy the fixed web server to a remote `Linux` virtual machine (VM).
- Test the deployed web server.

In simple words, you should be able to say:
>
> 1. I ran a web server locally on my computer and it worked!
> 2. I found and fixed a bug and the tests passed!
> 3. I deployed the web server on a remote VM and made it available to others!

## Tasks

### Prerequisites

1. [Lab setup](./lab/setup.md).

### Required

1. [Run the web server](./lab/tasks/required/task-1.md)
2. [Identify, report, and fix a bug](./lab/tasks/required/task-2.md)
3. [Run the web server using `Docker Compose`](./lab/tasks/required/task-3.md)
4. [Deploy the web server to the VM](./lab/tasks/required/task-4.md)

### Optional

1. [Implement the `/outcomes` endpoint](./lab/tasks/optional/task-1.md)
2. [Make your VM a proxy to your partner's web server](./lab/tasks/optional/task-2.md)
3. [Implement the post-order traversal](./lab/tasks/optional/task-3.md)

## Resolved Planning Decisions (Lab 3 redesign)

These decisions answer the current planning open questions for the upcoming Lab 3 scope.

1. Hardening depth:
   We require baseline hardening in Lab 3:
   - `PermitRootLogin no`
   - `PasswordAuthentication no`
   - non-root SSH user for operations
   - `ufw` enabled with required ports only
   - `fail2ban` enabled for SSH

2. Checkbot restrictions:
   In Lab 3, `checkbot` must be a dedicated no-sudo, key-only user.
   Command-restricted SSH keys can be added in Lab 4 if Lab 3 scope gets too heavy.

3. CI placement:
   CI is planned for Lab 4.

4. Security model:
   Lab 3 uses one shared API key for protected API resources.
   This is intentionally the simplest security model (no roles/permissions matrix in Lab 3).

5. Task split:
   Security is split across two tasks:
   - Task 5: API-key security
   - Task 6: VM hardening
   Deployment remains a separate final task.

6. Scope split if overloaded:
   - Lab 3 must keep API-key auth (single key, no roles).
   - Advanced hardening details and CI can move to Lab 4 when needed.
