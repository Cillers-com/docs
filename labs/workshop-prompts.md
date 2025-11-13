---
description: >-
  We are going use Bluetext to create a number of webapps using the prompts
  below. Starting from simple applications with just one service, we will move
  on to create more complex, full-stack webapps!
---

# Workshop Prompts

Feel free to experiment with your project if you finish generating before we move onto the next one together! Bluetext is designed to generate apps in an extendable way, which allows you to pick up the project from any time during the development with fresh context - whether you are coding solo or with an agent. We have created a git repository with final generated versions of each project, just incase you face issues with generation. You can access them from here: [https://github.com/dinoh100/WorkshopExperiments.git](https://github.com/dinoh100/WorkshopExperiments.git)

## 1. Portfolio Website

We are first going to create a portfolio website for a UX designer with project cards that show project details, skills developed, date, and more. We will also integrate Couchbase to store the project data.&#x20;

**Prompt 1:**&#x20;

{% code overflow="wrap" fullWidth="false" %}
```markup
Use Polytope to generate an API for a portfolio website using REST endpoints for the following resources: Project (fields: title, description, skills, started_at, finished_at).
```
{% endcode %}

**Prompt 2:**

{% code overflow="wrap" %}
```markup
Configure Couchbase to store the data and populate it with at least three example entries.
```
{% endcode %}

**Prompt 3:**

{% code overflow="wrap" %}
```markup
Create a frontend for our app
```
{% endcode %}

## 2. Zip File Compression Webapp

Now, we will make a full-stack webapp that allows you to upload a file, compress it to a zip file, and download the ZIP file.&#x20;

**Prompt 1:**

{% code overflow="wrap" %}
```markup
Implement a REST API for a file compression app with these endpoints:
- **POST /files**: Accept one or more files. Returns archiveId. 
- **GET /files**: Returns all uploaded fileIds on default. 
- **GET /files/{fileId}**: Returns the current state, metadata (filename, size, timestamps), and, when available, a download URL or location for the archive containing it.

- **GET /archives:** returns alls archiveIds.
- **GET /archives/{archiveId}**: Returns archive `state`, `metadata` (e.g., contained files, total size, timestamp), and `downloadUrl` (if `done`).
- **GET /archives/{archiveId}/download**: Direct download. Only available if `archive_completed`
```
{% endcode %}

**Prompt 2:**&#x20;

{% code overflow="wrap" %}
```markup
Create a frontend for our app.
```
{% endcode %}

**Prompt 3:**

{% code overflow="wrap" %}
```markup
Store newly zipped files into a couchbase database.
```
{% endcode %}

## 3. Snake Game!

For this app we are going to make a fun snake game, and have the scores stored persistently in Couchbase

**Prompt 1**

{% code overflow="wrap" %}
```markup
Prepare a REST API with scores as resource for a snake game.
```
{% endcode %}

**Prompt 2**

{% code overflow="wrap" %}
```markup
Set up Couchbase to store the high-scores.
```
{% endcode %}

**Prompt 3**

{% code overflow="wrap" %}
```markup
Generate a frontend to play the snake game.
```
{% endcode %}

## Temporal&#x20;

The next few projects will demonstrate how straightforward it is to get Temporal working with Bluetext. We will start by integrating Temporal into a project we already created, and will then move on to create some new projects from scratch with Temporal integration.

## 1. Temporal Integration with Zip Webapp

Now we will re-create our zip compression webapp, but this time we will be implementing Temporal from the beginning. Note that we are using a slightly different prompting style this time.

**Prompt 1:**

{% code overflow="wrap" %}
```
Implement a REST API for a file compression app with the following resources:
- Files (States: `uploading`, `archiving`, `deleting`, `deleted`, `failed`)
- Archives (States: `queued`, `compressing`, `idle`, `downloading`, `failed`)

Use temporal to manage state.
```
{% endcode %}

**Prompt 2:**&#x20;

{% code overflow="wrap" %}
```
Delete files when compressed into an archive, store archives in couchbase.
```
{% endcode %}

**Prompt 3:**&#x20;

{% code overflow="wrap" %}
```markup
Create a frontend for our app
```
{% endcode %}

## 2. Social Media Text Optimisation Webapp

For our final webapp, we are going to generate a webapp that takes text as an input, and re-articulates it in the styles of Linkedin, Twitter/X, and Instagram.&#x20;

Before prompting we must set the API key for open router. Do this by entering the following command in your terminal, in the same directory we will be creating the project from.

```
pt secrets set openrouter-api-key YOUR_API_KEY
```

**Prompt 1:**&#x20;

{% code overflow="wrap" %}
```
Implement an API for an app that uses AI to rephrase text in the styles of Linkedin, Twitter, and Instagram. Setup the API to retrieve a open router API key through an environment variable for the text generation. Chose gemini 2.5 pro as the model to generate the text. Once you added the API service, you can inject the open router API key by adding the line `- { name: OPENROUTER_API_KEY, value: pt.secret openrouter-api-key }` to the modules `polytope.yml` file. The API will have the following endpoints: 

POST /api/jobs 
GET /api/jobs/{jobId}/status 
GET /api/jobs/{jobId}/twitter 
GET /api/jobs/{jobId}/linkedin 
GET /api/jobs/{jobId}/instagram 

States should be managed with Temporal
```
{% endcode %}







