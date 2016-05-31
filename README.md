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

* `/stores` (Filialen, [example](examples/stores.json))
* `/store-channels` (Filialkanäle, [example](examples/store-channels.json))
* `/store-services` (Filialangebote, [example](examples/store-services.json))

### Articles/Promotions

* `/article-groups` (Warengruppen, [example](examples/article-groups.json))
* `/articles` (Artikel, [example](examples/articles.json))
* `/advertised-articles` (beworbene Artikel)
* `/promotion-types` (Aktionstypen, [example](examples/promotion-types.json))

### Online Advertising

* `/online-publications` (Online-Werbemittel, [example](examples/online-publications.json))
* `/online-filters` (Angebotsfilter, [example](examples/online-filters.json))
* `/online-groups` (Internet-Sortimente, [example](examples/online-groups.json))

### Screen Advertising
* `/screen-publications` (Screen-Werbemittel, [example](examples/screen-publications.json))
* `/screen-stores` (Screen-Filialen, [example](examples/screen-stores.json))

### Appraisals
* `/appraisals` (Wein-Bewertungen, [example](examples/appraisals.json))
* `/appraisals/{appraisal_id}` (Wein-Bewertung, [example](examples/appraisal.json))
* `/appraisal-statistic/{date}` (Wein-Bewertungen Statistik, [example](examples/appraisal-statistic.json))
* `/sweepstake-participants` (Verlosung-Teilnehmer, [example](examples/sweepstake-participants.json))

## Building

### Protobox
To build the specification we're using [swagger-codegen](https://github.com/swagger-api/swagger-codegen).

Run the following commands in [Protobox](https://bitbucket.org/detailnet/protobox) to install it (and it's dependencies):

        sudo apt-get install maven
        sudo apt-get install openjdk-7-jdk
        git clone git@github.com:swagger-api/swagger-codegen.git
        cd swagger-codegen
        mvn package

#### JSON
Once installed, `swagger.json` can be generated as follows:

        java -jar modules/swagger-codegen-cli/target/swagger-codegen-cli.jar generate \
            -i ../denner-portal-api-spec/src/swagger.yml \
            -l swagger \
            -o ../denner-portal-api-spec/build/swagger
        
The file will be located at `build/swagger/swagger.json`.

#### HTML
You can also generate a static HTML page:

        java -jar modules/swagger-codegen-cli/target/swagger-codegen-cli.jar generate \
            -i ../denner-portal-api-spec/src/swagger.yml \
            -l html \
            -o ../denner-portal-api-spec/build/html
            
The file will be located at `build/html/index.html`.
