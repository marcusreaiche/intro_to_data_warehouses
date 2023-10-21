# Introduction to Data Warehouses

This is part of [Udacity's Data Engineering with AWS Nanodegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027).

This repository makes it easy to run the Notebooks locally instead of using the course workspace.

# Running Postgres locally

One needs to install Docker and Docker Compose (for Linux users) to be able to spin up the docker containers using the provided `docker-compose.yml` file.

Follow this [link](https://www.docker.com/products/docker-desktop/) for the installation of Docker Desktop.

After that, create a `.env` file in the project directory setting the Postgres environment variables For an example take a look at `example.env`:

```
POSTGRES_PASSWORD=123456
```

Then, run the following command in the terminal:

```bash
$ docker-compose up -d
```

Check that the containers are running by executing:

```bash
$ docker ps
```

You can run Postgres CLI inside the pagila container by executing:

```bash
$ docker exec -it pagila psql -U postgres
```

The prompt should look like

```bash
postgres=#
```

List all the tables by executing:

```bash
postgres=# \dt
```

This should output the following:

```
             List of relations
 Schema |     Name      | Type  |  Owner   
--------+---------------+-------+----------
 public | actor         | table | postgres
 public | address       | table | postgres
 public | category      | table | postgres
 public | city          | table | postgres
 public | country       | table | postgres
 public | customer      | table | postgres
 public | film          | table | postgres
 public | film_actor    | table | postgres
 public | film_category | table | postgres
 public | inventory     | table | postgres
 public | language      | table | postgres
 public | payment       | table | postgres
 public | rental        | table | postgres
 public | staff         | table | postgres
 public | store         | table | postgres
(15 rows)
```

Likewise, run Postgres CLI inside the pagila-star container by executing:

```bash
$ docker exec -it pagila psql -U postgres
```

Listing all the tables:

```bash
postgres=# \dt
```

we obtain:

```
             List of relations
 Schema |     Name      | Type  |  Owner   
--------+---------------+-------+----------
 public | actor         | table | postgres
 public | address       | table | postgres
 public | category      | table | postgres
 public | city          | table | postgres
 public | country       | table | postgres
 public | customer      | table | postgres
 public | dimcustomer   | table | postgres
 public | dimdate       | table | postgres
 public | dimmovie      | table | postgres
 public | dimstore      | table | postgres
 public | factsales     | table | postgres
 public | film          | table | postgres
 public | film_actor    | table | postgres
 public | film_category | table | postgres
 public | inventory     | table | postgres
 public | language      | table | postgres
 public | payment       | table | postgres
 public | rental        | table | postgres
 public | staff         | table | postgres
 public | store         | table | postgres
(20 rows)
```

Note the additional fact and dimension tables. These tables are built in the Notebooks L1 E1 from steps 1 to 5.

# Creating Python environment

A `conda.yml` is provided to create a conda virtual environment using [miniconda3](https://docs.conda.io/projects/miniconda/en/latest/miniconda-install.html).

Execute the command:

```bash
$ conda env create -f conda.yml
```

to create the `intro-to-dw` environment.

Activate it by running:

```bash
$ conda activate intro-to-dw
```