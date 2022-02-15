# Wordpress Automatizálás

A jelen leírás követése megalapozza a következő wordpress oldal generálását későbbi automatizálás céljából

## Alapozó műveletek

composer init 

composer require johnpbloch/wordpress 

git init

composer.json

## Composer.json módosítása

Az alábbi sorok hozzáadása szükséges, hogy a generált wordpress mappába importálja majd be az alább jelölt függőségeket.

```
"repositories": [
        {
            "type":"composer",
            "url":"https://wpackagist.org",
            "only":[
                "wpackagist-plugin/*",
                "wpackagist-theme/*"
            ]
        }
    ],
    "extra": {
        "installer-paths": {
            "wordpress/wp-content/mu-plugins/{$name}/": [
                "wpackagist-plugin/akismet"
            ],
            "wordpress/wp-content/plugins/{$name}/": [
                "type:wordpress-plugin"
            ],
            "wordpress/wp-content/themes/{$name}/": [
                "type:wordpress-theme"
            ]
        }
    }
```

## Generált fájlok levétele a verziókezelés alól

```
vendor/
wordpress/
```

Mindezek után a projekt készen áll az automatikus függőségkezelésre.
