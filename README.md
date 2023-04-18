<p align="center">
  <img width="500" src="https://user-images.githubusercontent.com/10407788/204477834-2533241a-5927-4f56-959e-4e8494027bc0.png"/>
  <p align="center">Simple and Fast Geospatial OGC Features and Tiles API for PostGIS.</p>
</p>
<p align="center">
  <a href="https://github.com/developmentseed/tipg/actions?query=workflow%3ACI" target="_blank">
      <img src="https://github.com/developmentseed/tipg/workflows/CI/badge.svg" alt="Test">
  </a>
  <a href="https://codecov.io/gh/developmentseed/tipg" target="_blank">
      <img src="https://codecov.io/gh/developmentseed/tipg/branch/main/graph/badge.svg" alt="Coverage">
  </a>
  <a href="https://pypi.org/project/tipg" target="_blank">
      <img src="https://img.shields.io/pypi/v/tipg?color=%2334D058&label=pypi%20package" alt="Package version">
  </a>
  <a href="https://github.com/developmentseed/tipg/blob/main/LICENSE" target="_blank">
      <img src="https://img.shields.io/github/license/developmentseed/tipg.svg" alt="License">
  </a>
</p>

---

**Documentation**: <a href="https://developmentseed.org/tipg/" target="_blank">https://developmentseed.org/tipg/</a>

**Source Code**: <a href="https://github.com/developmentseed/tipg" target="_blank">https://github.com/developmentseed/tipg</a>

---

`tipg`, pronounced *T[ee]pg*, is a **python** package which helps creating lightweight OGC **Features** and **Tiles** API with PostGIS Database backend. The API has been designed with respect to [OGC Features](https://ogcapi.ogc.org/features) and [OGC Tiles](https://ogcapi.ogc.org/tiles/) specifications.

> **Note**
> This project is the result of the merge between [tifeatures](https://github.com/developmentseed/tifeatures) and [timvt](https://github.com/developmentseed/timvt).

## Install

```bash
$ python -m pip install pip -U
$ python -m pip install tipg

# or from source
$ git clone https://github.com/developmentseed/tipg.git
$ cd tipg
$ python -m pip install -e .
```

## OGC Specifications

Specification | Status | link |
|          -- |     -- |   -- |
OGC Common Part 1: Core                |  ✅ | https://docs.ogc.org/DRAFTS/19-072.html
OGC Common Part 2: Geospatial Data     |  ✅ | http://docs.ogc.org/DRAFTS/20-024.html
OGC Features Part 1: Core              |  ✅ | https://docs.ogc.org/is/17-069r4/17-069r4.html
OGC Features Part 2: CRS by Reference  |  ❌ | https://docs.ogc.org/is/18-058r1/18-058r1.html
OGC Features Part 3: Filtering / CQL2  |  ✅ | https://docs.ogc.org/DRAFTS/19-079r1.html
OGC Tiles Part 1: Core                 | WIP | https://docs.ogc.org/is/20-057/20-057.html

Notes:

The project authors choose not to implement the Part 2 of the specification to avoid the introduction of CRS based GeoJSON. This might change in the future.

While the authors tried to follow OGC specifications to the letter, some API endpoints might have more capabilities (e.g geometry column selection).

## PostGIS/PostgreSQL

`tipg` rely a lot of `ST_*` PostGIS functions. You need to make sure your PostgreSQL database has PostGIS installed.

```sql
SELECT name, default_version,installed_version
FROM pg_available_extensions WHERE name LIKE 'postgis%' or name LIKE 'address%';
```

```sql
CREATE EXTENSION postgis;
```

### Configuration

To be able to work, the application will need access to the database. `tipg` uses [starlette](https://www.starlette.io/config/)'s configuration pattern which make use of environment variable and/or `.env` file to pass variable to the application.

Example of `.env` file can be found in [.env.example](https://github.com/developmentseed/tipg/blob/main/.env.example)

```
# you need define the DATABASE_URL directly
DATABASE_URL=postgresql://username:password@0.0.0.0:5432/postgis
```

More info about configuration options in https://developmentseed.org/tipg/advanced/configuration/

## Launch

```bash
$ pip install uvicorn

# Set your postgis database instance URL in the environment
$ export DATABASE_URL=postgresql://username:password@0.0.0.0:5432/postgis
$ uvicorn tipg.main:app

# or using Docker

$ docker-compose up
```

<p align="center">
  <img width="700" src="https://user-images.githubusercontent.com/10407788/204860360-f38d7d11-6fde-4618-b318-c31041d4e526.png"/>
  <img width="700" src="https://user-images.githubusercontent.com/10407788/232048615-d52224fa-c9d0-4844-a993-79062dbef5b8.png"/>
  <img width="700" src="https://user-images.githubusercontent.com/10407788/204860378-75b89da8-28b8-4f6d-963e-2a8c01866203.png"/>
  <img width="700" src="https://user-images.githubusercontent.com/10407788/232049901-02b9da10-e749-4430-a690-2fcc0e79bac8.png"/>
  <img width="700" src="https://user-images.githubusercontent.com/10407788/232050087-1693d8ae-fb13-4d97-b33a-8d42624aea3e.png"/>
</p>

## Contribution & Development

See [CONTRIBUTING.md](https://github.com/developmentseed/tipg/blob/main/CONTRIBUTING.md)

## License

See [LICENSE](https://github.com/developmentseed/tipg/blob/main/LICENSE)

## Authors

Created by [Development Seed](<http://developmentseed.org>)

## Changes

See [CHANGES.md](https://github.com/developmentseed/tipg/blob/main/CHANGES.md).

