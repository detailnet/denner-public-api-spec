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

To see the documentation page [Swagger UI](https://swagger.io/tools/swagger-ui/) visit  http://denner-mobile-api-docs.detailnet.ch/ or 
for development start the Docker instance that presents the static HTML pages in `/docs`  (`lando start` and then view http://denner-mobile-api-spec.detailnet.me/)

### Building
To build the specification we're using [swagger-codegen](https://github.com/swagger-api/swagger-codegen).

#### Using Ubuntu on WSL2 
Run the following commands to install swagger-codgen and it's dependencies in a separate directory:

        cd ..
        git clone git@github.com:swagger-api/swagger-codegen.git
        sudo apt-get install maven
        sudo apt install openjdk-11-jdk
        cd swagger-codegen
        git fetch origin 3.0.0:3.0.0
        git checkout 3.0.0
        #  export JDK_JAVA_OPTIONS=-Djdk.attach.allowAttachSelf=true .. not sure if really needed
        mvn clean package

#### JSON (used to update docs page too)
Once installed, `openapi.json` can be generated as follows:

        cd ../swagger-codegen  && \
        java -jar modules/swagger-codegen-cli/target/swagger-codegen-cli.jar generate \
            -i ../denner-public-api-spec/src/swagger.yml \
            -l openapi \
            -o ../denner-public-api-spec/docs && \
        cd -

The file will be located at `docs/openapi.json`.

**Important: after generation revert the servers section at beginning of `docs/openapi.json`**

You can then review the changes in the local browser (`lando start` and then view http://denner-public-api-spec.detailnet.me/) and commit them.

#### Compiling Stylesheets

To compile the stylesheets for the swagger docs, globally install npm sass with `install -g sass` and run sass:

        sass docs/style/main.scss docs/swagger-ui.css --style=compressed

For continuous watch and build during development run:

        sass docs/style/main.scss docs/swagger-ui.css --watch
