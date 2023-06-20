# Denner Public API Spec

## Terms and translations
Consider the following terms:

| DE          | EN          |
|-------------|-------------|
| Artikel     | Article     |
| Werbemittel | Publication |
| Aktion      | Promotion   |
| bewerben    | advertise   |
| Filiale     | store       |

## Data and resources
The Denner Public API provides open data around the promotion of it's articles.

### Promotion

* `/online-articles` (Artikel, [example](examples/online-articles.json))

### Stores

* `GET /stores` (Filialen, [example](examples/stores.json))

## Documentation and Building

To see the documentation page [Swagger UI](https://swagger.io/tools/swagger-ui/) visit  http://denner-api-docs.detailnet.ch/ 
or for development, start the Docker instance (`lando start`) that presents the static HTML pages in `/docs` directory and
load the page http://denner-public-api-spec.detailnet.me. 

### Building
To build the specification we're using [swagger-codegen](https://github.com/swagger-api/swagger-codegen).

This project is already setup to build directly through `lando`.

```shell
lando start
lando build-docs
```

The file will be located at `docs/openapi.json`.

**Important: after generation revert the servers section at beginning of `docs/openapi.json`**

You can then review the changes in the [local browser](http://denner-public-api-spec.detailnet.me/) before commit.

### Preserve AWS API changes

AWS API gateway does a good job with the "Deployment History" but for a better consultation on changes and in case of disaster recovery,
we download in this project the export as "OpenAPI 3 + API Gateway Extensions" after every deployment.

The download is performed with `lando export-api`. (Can be also dane manually through the AWS console)


### Compiling Stylesheets

To compile the stylesheets for the swagger docs, globally install npm sass with `install -g sass` and run sass:

        sass docs/style/main.scss docs/swagger-ui.css --style=compressed

For continuous watch and build during development run:

        sass docs/style/main.scss docs/swagger-ui.css --watch
