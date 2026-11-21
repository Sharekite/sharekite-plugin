---
name: publish-and-share
description: Publishes pages, reports, and static sites with Sharekite and shares them by link or by email invitation. Use when the user wants to put work online or update it, get a link to send, share work with named people, or check who can open it, whether invitations were sent, or which work has unpublished changes. Not for server code, databases, packages, or email attachments.
---

# Publish and share with Sharekite

The user's explicit instructions on names, files, and steps take precedence over the defaults in this skill.

## Publish only with the user's choice

- Publish and change access only when the user asks.
- When the user has not said who can open the work, ask before the first publication: anyone with the link, only people the user names by email address, or anyone with a password. Do not choose an audience or infer recipients.
- Pass a password only when the user gave one. When the result contains a password, give it to the user.

## Set up

When the Sharekite tools are not available, tell the user that Sharekite is not connected, and ask them to connect it and sign in. Setup steps for each client: https://www.sharekite.app/connect/. Continue with the user's request after `list_projects` succeeds.

## Choose the tools for the job

- **Publish new work:** `list_projects` to check that the work is not on Sharekite yet, then `create_project`, `upload`, then `publish` with the uploaded version.
- **Share work, or change who can open it:** `list_projects`, then `publish` without a version. When the work is not on Sharekite yet, publish it as new work. When the project has no published version, call `publish` with its latest version and the audience. When `publish` answers `not_restricted`, tell the user who can open the work now, and ask before you change the audience.
- **Update published work:** `list_projects`, `get_files` when you do not have the current files, `upload`, then `publish` with the new version.
- **Check access and invitations:** `list_projects`, then `get_project`. Change nothing.
- **Find work with unpublished changes:** `list_projects`. A project has unpublished changes when its `latestVersion` is not null and its `publishedVersion` is null or lower.

## Find the project

Match the user's words to the project names from `list_projects`. When several projects match, ask the user which one to use. When none matches, tell the user, unless the request is to publish or share work that you have; that is new work.

## Prepare the files

- Pass a short name of the work to `create_project`, such as "Q3 client report". The name sets the project key and the address.
- Send only the static files that the site serves: HTML, CSS, JavaScript, images, fonts, and documents. When the work needs a build step, build it and upload the output.
- Before you upload, check that each local `href`, `src`, and CSS `url()` points to a file in the upload, at the same relative path. Add a missing file or fix the path. When you cannot find a file, list the broken references and ask the user whether to publish anyway.

## Report

- After each upload, give the preview link. After each `publish`, give the audience and the status of each invitation.
- Give the address of each project that you name.
- Copy links exactly as the tools return them. Do not build a link from a project key.
