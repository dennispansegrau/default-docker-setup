# Default Docker Setup
### PHP 8.1 (incl. Xdebug) + MariaDB + nginx

**Setup**:
* Set the database credentials in the **docker-compose.yml**.
* Replace **PROJECT** with a project name / test domain in the **docker/nginx/default.conf**.
* Add the test domain e.g. **127.0.0.1 example.local** to **/etc/hosts**.

**Hint**: The document root is set to **/var/www/html/public** and must be changed perhaps.


