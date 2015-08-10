restful-clojure
===============

An example RESTful shopping list application back-end written in Clojure to accompany a tutorial series on kendru.github.io

Setup
-----

    createuser --pwprompt restful_dev
    createdb -Orestful_dev -Eutf8 restful_dev

    export RESTFUL_DB_URL="jdbc:postgresql://localhost:5432/restful_dev?user=restful_dev&password=pass_dev"

    lein ragtime migrate


Walk-Through
------------

Now start the server:

    lein ring server

... and create a sample user:


    http POST :3000/users name=niko email=test@exmaple.org level=admin password=test123

Get an access token for this user:

    http POST :3000/sessions user-id=2 password=test123

Now try with this user to access a resource which is secured by providing the authorization header as follows:

    http :3000/products 'Authorization:Token J7NSvJd0Cgi99aRogkibxyKyNGJOxhFW7FdQbzchGRU='