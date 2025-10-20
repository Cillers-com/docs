---
description: >-
  We are going use Bluetext to create a number of webapps using the prompts
  below. Starting from simple applications with just one service, we will move
  on to create more complex, full-stack webapps!
---

# Workshop Prompts

## 1. Portfolio Website

We are going to create a portfolio website for a UX designer with project cards that show project details, skills developed, the date, and more. We will also integrate couchbase to store the project data.&#x20;

**Prompt 1:**&#x20;

{% code overflow="wrap" fullWidth="true" %}
```markup
Use Polytope to generate an API for a portfolio website using REST endpoints for the following resources: Project (fields: title, description, skills, started_at, finished_at). Configure Couchbase to store the data and populate it with at least three example entries.
```
{% endcode %}

**Prompt 2:**

{% code overflow="wrap" %}
```markup
Create a frontend for our app
```
{% endcode %}

## 2. Zip File Compression Webapp

Now, we will make a full-stack webapp that allows you to upload a file, compress them to a zip file, and download the ZIP file.&#x20;

**Prompt 1:**

{% code overflow="wrap" %}
```markup
Implement a REST API for a file compression app with these endpoints:
- **POST /files**: Accept one or more files. Returns archiveId. 
- **GET /files**: Returns all uploaded fileIds on default. 
- **GET /files/{fileId}**: Returns the current state, metadata (filename, size, timestamps), and, when available, a download URL or location for the archive containing it.

- **GET /archives:** returns alls archiveIds.
- **GET /archives/{archiveId}**: Returns archive `state`, `metadata` (e.g., contained files, total size, timestamp), and `downloadUrl` (if `done`).
- **GET /archives/{archiveId}/download**: Direct download. Only available if `archive_completed`.
Store archives in Couchbase. Delete uncompressed files when finished processing. 
```
{% endcode %}

**Prompt 2:**&#x20;

{% code overflow="wrap" %}
```markup
create a frontend for our app.
```
{% endcode %}

**Prompt 3:**

{% code overflow="wrap" %}
```markup
Store newly zipped files into a couchbase database.
```
{% endcode %}

## 3. Snake Game!

For this app, we are going to make a fun snake game, and have the scores stored persistently in CouchBase

**Prompt 1**

{% code overflow="wrap" %}
```markup
Prepare a REST API with scores as resource for a snake game.
```
{% endcode %}

**Prompt 2**

{% code overflow="wrap" %}
```markup
Generate a frontend to play the snake game
```
{% endcode %}

## Temporal&#x20;

The next few projects will demonstrate how straightforward it is to get Temporal working with Bluetext. We will start by integrating it into projects we already created, and then go on to Create some new projects with Temporal.

## 1. Temporal Integration with Zip Webapp

Now we will re-create our Zip Compression webapp, whilst implementing Temporal from the beginning.

Prompt 1:

{% code overflow="wrap" %}
```
Implement a REST API for a file compression app with these endpoints:
- **POST /files**: Accept one or more files. Returns archiveId. 
- **GET /files**: Returns all uploaded fileIds on default. 
- **GET /files/{fileId}**: Returns the current state, metadata (filename, size, timestamps), and, when available, a download URL or location for the archive containing it.

- **GET /archives:** returns alls archiveIds.
- **GET /archives/{archiveId}**: Returns archive `state`, `metadata` (e.g., contained files, total size, timestamp), and `downloadUrl` (if `done`).
- **GET /archives/{archiveId}/download**: Direct download. Only available if `archive_completed`.

Store all files in memory. Delete them when processed. 

Use Temporal to manage all state and long‑running tasks:

Files
- `uploading` 
- `archiving` 
- `deleting` 
- `done` 
- `failed`

Archives
- `queued`
- `compressing`
- `done`
- `downloading`
- `failed`
```
{% endcode %}

Prompt 2:&#x20;

{% code overflow="wrap" %}
```markup
create a frontend for our app.
```
{% endcode %}

Prompt 3:

{% code overflow="wrap" %}
```markup
Store newly zipped files into a CouchBase database.
```
{% endcode %}

## 2. Clothes Ordering E-Commerce Platform with Temporal Integration

We will now create a webapp that allows you to place orders on a clothing website, switch to admin view to manage orders, and manage workflows with temporal.

Prompt 1: \
Generate an API for a clothes ordering platform with the following REST endpoints\


&#x20;**`GET /api/products`**&#x20;

**`POST /api/orders`**&#x20;

**`GET /api/orders`**&#x20;

Add Temporal to the API to mange order state changes (uploading, compressing, completed), and store clothing Items in Couchbase

Prompt 2:



