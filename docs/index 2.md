---
layout: default
title: 1. Get started
nav_order: 1
description: "RSD-as-a-Service Documentation"
permalink: /
---
![image](https://user-images.githubusercontent.com/4195550/136156498-736f915f-7623-43d2-8678-f30b06563a38.png)

# RSD-as-a-service Documentation
{: .fs-9 }

To promote the visibility, impact and reuse of research software.
{: .fs-6 .fw-300 }

[View it on GitHub](https://github.com/research-software-directory/RSD-as-a-service){: .btn .fs-5 .mb-4 .mb-md-0 }

---
{: .no_toc }
## Monorepo
The RSD-as-a-Service project is a divided into different services included in the monorepo.

|-- CITATION.cff
|-- CODE_OF_CONDUCT.md
|-- CONTRIBUTING.md
|-- LICENSE
|-- README.md
|-- authentication
|-- backend-postgrest
|-- data-migration
|-- database
|-- deployment
|-- docker-compose.yml
|-- docs
|-- frontend
|-- nginx
|-- node_modules
`-- scrapers


## Dependencies
To run the application locally you need to install the following dependencies:
- Docker

## Get Started


### Environment variables

The environment variables should be stored in .env file, which is automatically loaded by docker-compose. To validate loading of env variables use `docker-compose config`. More info about use of enviroment variables in docker-compose is available at [official documentation](https://docs.docker.com/compose/environment-variables/)

- copy the file `.env.example` to `.env` file at the root of the project

```bash
# from project root dir
cp .env.example .env
```

- You need to modify the new .env file with the corresponding value secrets.
- build local images

```bash
# from project root dir
docker-compose build
```

## Running locally

Run the command `docker-compose up`.

```bash
# from project root dir
docker-compose up
```

The application can be viewed on http://localhost

### Frontend with hot-module-replacement (HMR)

To run frontend in the development mode with the hot-module-replacement (HMR) you should start additional instance of the frontend which will be available at http://localhost:3000

```bash
# navigate to frontend folder
cd frontend
# install dependencies
yarn install
# start fe in dev mode
yarn dev
```

More information about frontend setup is [available in the frontend readme file](/frontend/README.md).

## Clear/remove data (reset)

To clear the database, if the database structure has changed or you need to run data migration again, run the command:

```bash
docker-compose down --volumes
```

## Data migration

A data migration script is available to migrate data from the legacy RSD to the new one:

- run current RSD solution using `docker-compose up` from the root of the project
- run the migration script using docker-compose file in the data-migration folder

```bash
# navigate to data-migration folder
cd data-migration
# run data migration docker-compose file
docker-compose up
```

More information about [data migration is avaliable here](data-migration/README.md).

## Tech Stack

![image](/rsd-stack-220304.png)







#### Thank you to the contributors of Just the Docs!

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"/></a>
  </li>
{% endfor %}
</ul>


### Code of Conduct

Just the Docs is committed to fostering a welcoming community.

[View our Code of Conduct](https://github.com/just-the-docs/just-the-docs/tree/main/CODE_OF_CONDUCT.md) on our GitHub repository.
