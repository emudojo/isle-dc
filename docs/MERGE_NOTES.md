## How to run your own app

* make folder 'codebase`
* git clone your site into it 
* copy in the new config/drupal/settings.php.local directly into your drupal app (we'll figure out the bind-mount later)
* boot the system up with `make up`, and don't care that drupal keeps crashing. when we have the database in place it will stop. Notice that the "drupal" container is baked by the drupal.Dockerfile in this project, so you can edit that if you need to install other dependencies/etc.
* docker cp your database in and import it (root/password will work; db name is drupal_default)
* Hopefully composer will do a good job on your build. If not, run `COMPOSER_MEMORY_LIMIT=-1 composer install` on the drupal service.
* `make down` will shut things off. `make clean` will clean it all up. If you want to run dc commands manually, just remember to use `-p islandora` (see Makefile for examples).