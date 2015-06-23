# Denner Portal 2.0 API Spec

## Terms and translations
Consider the following terms:

| DE          | EN          |
|-------------|-------------|
| Filiale     | Store       |
| Artikel     | Article     |
| Werbemittel | Publication |
| Aktion      | Promotion   |
| bewerben    | advertise   |

## Data and resources
The Denner Portal provides mostly advertising related data.

### Stores

* `/stores` (Filialen)
* `/store-channels` (Filialkanäle)
* `/store-services` (Filialangebote)

### Articles/Promotions

* `/article-groups` (Warengruppen)
* `/articles` (Artikel)
* `/advertised-articles` (beworbene Artikel)
* `/promotions-types` (Aktionstypen)

### Online-Publications

* `/online-publications` (Werbemittel)
* `/online-filters` (Angebotsfilter)
* `/online-groups` (Internet-Sortimente)


## Building

### Protobox
To create a `swagger.json` file we're using [swagger-codegen](https://github.com/swagger-api/swagger-codegen).

Run the following commands in [Protobox](https://bitbucket.org/detailnet/protobox) to install it (and it's dependencies):

        sudo apt-get install maven
        sudo apt-get install openjdk-7-jdk
        git clone git@github.com:swagger-api/swagger-codegen.git
        cd swagger-codegen
        mvn package

Once installed, `swagger.json` can be generated as follows:

        java -jar modules/swagger-codegen-cli/target/swagger-codegen-cli.jar generate \
            -i ../denner-portal-api-spec/src/swagger.yml \
            -l swagger \
            -o ../denner-portal-api-spec/build/swagger
        
The file will be located at `build/swagger/swagger.json`.
