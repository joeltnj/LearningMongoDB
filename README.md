
# Installation de Docker et création des conteneurs

Pour installer Docker et créer des conteneurs, suivez ce [lien](https://docs.docker.com/desktop/install/windows-install/).
```{bash}
https://docs.docker.com/desktop/install/windows-install
```
Une fois que l'installation est terminée, exécutez les commandes suivantes dans l'invite de commande Windows pour mettre en place MongoDB à l'aide de Docker.  J'espère que personne ne manque de Windows sur son PC😆😆

```{bash}
docker run -d --name mon_instance_mongo -p 27017:27017 mongo:4.4.18
```

Ensuite, exécutez la commande suivante pour installer un conteneur permettant d'utiliser MongoDB via une interface similaire à phpMyAdmin (on va se rappeler de l'annee derniere). Assurez-vous de modifier les identifiants dans la commande ci-dessous.Dans ce tutos j'ai utiliseé mes identifiants comme name: "joe" avec le mot de passe : "0003". Ne pensez surtout pas à me hacker. 😆😆

```{bash}
docker run -it --rm --name mongo-express -p 8081:8081 -e ME_CONFIG_MONGODB_SERVER=host.docker.internal -e ME_CONFIG_BASICAUTH_USERNAME=joe -e ME_CONFIG_BASICAUTH_PASSWORD=0003 mongo-express
```

Vous pouvez MAINTENANT accéder à votre base de données MongoDB dans votre navigateur via l'URL :

```{bash}
 http://localhost:8081.
```

Si vous préférez une version de bureau, vous pouvez télécharger MongoDB Compass via le url ci dessous. LOl, d'ailleurs je connais un(e) qui aime ce genre d'interface, mais je ne citerai pas son nom 😆

```{bash}
https://www.mongodb.com/try/download/compass
```
Pour vous connecter à MongoDB en utilisant Python, exécutez la commande suivante dans l'invite de commande :


```{bash}
pip install pymongo
```
Ensuite, créez un fichier .py et utilisez le code suivant pour vous connecter à la base de données et effectuer des opérations :


```{bash}
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")

db = client["myDB"]
collection = db["myTable"]

data = {"key": "value"}
collection.insert_one(data)

# result = collection.find({})
# for doc in result:
#     print(doc)

```

Ceci n'est qu'un démarrage rapide avec MongoDB, le reste vous devrez vous documenter en sur Internet.

Facile noooon 😉😉








