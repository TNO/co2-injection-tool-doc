Installation
==================

Cloud
----------------------------------------
    * *only accessible during testing period 1-Feb-2023 to 1-Apr-2023*
    * You can access the tool via this website  `http://tnoco2tool.northeurope.cloudapp.azure.com:5100/ <http://tnoco2tool.northeurope.cloudapp.azure.com:5100/>`_

Local Premises
----------------------------------------

   * You need Docker (`Docker website <https://www.docker.com/products/docker-desktop/>`_) installed in your computer
   * Create docker-compose.yml file in your folder

   .. code-block:: yaml

      version: '3.8'
      services:
         co2tool:
           image: ci.tno.nl/htfd/co2tool:latest
           ports:
             - 5100:5100
           environment:
             - PYTHONUNBUFFERED=1
             - FLASK_DEBUG=1
             - CELERY_BROKER_URL=redis://redis:6379/0
             - CELERY_RESULT_BACKEND=redis://redis:6379/0
             - MYSQL_URL=mysql://root:123456@mysql:3306/co2tool_db
           restart: unless-stopped
           volumes:
             - simulation-db:/opt/simulation
             - project-db:/opt/projectdata

         worker:
           image: ci.tno.nl/htfd/co2tool:celeryworker
           environment:
             - PYTHONUNBUFFERED=1
             - CELERY_BROKER_URL=redis://redis:6379/0
             - CELERY_RESULT_BACKEND=redis://redis:6379/0
             - MYSQL_URL=mysql://root:123456@mysql:3306/co2tool_db
           restart: unless-stopped
           volumes:
             - simulation-db:/opt/simulation
             - project-db:/opt/projectdata

         redis:
           image: redis:6-alpine
           ports:
               - 6379:6379
           restart: unless-stopped

         mysql:
           image: mysql:8.0
           ports:
             - 3306:3306
           environment:
             - MYSQL_ROOT_PASSWORD=123456
             - MYSQL_DATABASE=co2tool_db
           restart: unless-stopped
           volumes:
             - mysql-db:/var/lib/mysql

      volumes:
        mysql-db:
        simulation-db:
        project-db:

   * Start the program: *docker-compose up -d*
   * The tool is accessible via this URL `http://localhost:5100/ <http://localhost:5100/>`_
