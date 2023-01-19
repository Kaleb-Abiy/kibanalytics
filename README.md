# Kibanalytics

This project aims to make use of the ELK stack to collect events from web pages and visualize them, offering the same kind of insights that Google Analytics does.

The reason behind this project is to provide an alternative to GA that offers data ownership, adblocker avoidance, powerful aggregations, grained filtering and big data storage.

For full documentation, check [https://kibanalytics.io/](https://kibanalytics.io/)

## Quick Start

### Requirements

Host server with the following installed software:

- [Git](https://git-scm.com/)
- [Docker-Compose](https://docs.docker.com/compose/)

### Step-By-Step

#### 1. Download Kibanalytics Code Repository

```bash
git clone https://github.com/kibanalytics/kibanalytics.git
cd kibanalytics
```

#### 2. Copy Default Configuration Files

By default, all CORS origins are allowed to call Kibanalytics back-end server.

```bash
cp .env.example .env
cp -r .config.example .config
```

It's recomended to change the default EXPRESS_SESSION_SECRET environment variable value
if running Kibanalytics in production.

#### 3. Start Docker Services

```bash
docker-compose --profile local --profile production up -d --build
```

#### 4. Load Default Dashboards

```bash
docker-compose exec node npm run load-dashboards
```

#### 5. Add Front-End Tracking Library

It's recomended to change the EXPRESS_SESSION_SECRET and ELASTICSEARCH_PASSWORD environment variables default values
before running Kibanalytics in production.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My Website To Track</title>
    <script src="http://localhost:3000/kbs.js" 
            data-server-url="http://localhost:3000/collect">
    </script>
    ...
</head>
<body>
    <h1>My Website Header</h1>
    <main>My Website Main Content</main>
...
</body>
</html>
```

Alternatively you can access [http://localhost:3000](http://my-kibanalytics-server-host:3000) to interact with some example pages.

#### 6. Open Example Dashboard

By accessing [http://localhost:5601/app/dashboards](http://localhost:5601/app/dashboards).