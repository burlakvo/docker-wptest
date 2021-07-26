# docker-wptest

Run WordPress tests in a Docker container.

Installed WordPress versions with right test library for each versions:

<details>
  <summary>4.x.x</summary>
  
  |4.4.x|4.5.x|4.6.x|4.7.x|4.8.x|4.9.x |
  |-----|-----|-----|-----|-----|------|
  |4.4  |4.5  |4.6  |4.7  |4.8  |4.9   |
  |4.4.1|4.5.1|4.6.1|4.7.1|4.8.1|4.9.1 |
  |4.4.2|4.5.2|     |4.7.2|4.8.2|4.9.2 |
  |4.4.3|4.5.3|     |4.7.3|4.8.3|4.9.3 |
  |4.4.4|4.5.4|     |     |     |4.9.4 |
  |4.4.5|     |     |     |     |4.9.5 |
  |     |     |     |     |     |4.9.6 |
  |     |     |     |     |     |4.9.7 |
  |     |     |     |     |     |4.9.8 |
  |     |     |     |     |     |4.9.9 |
  |     |     |     |     |     |4.9.10|
  |     |     |     |     |     |4.9.11|
  |     |     |     |     |     |4.9.12|
  |     |     |     |     |     |4.9.13|
  |     |     |     |     |     |4.9.14|
  |     |     |     |     |     |4.9.15|
  |     |     |     |     |     |4.9.16|

</details>

<details>
  <summary>5.x.x</summary>

  |5.0.x |5.1.x|5.2.x|5.3.x|5.4.x|5.5.x|5.6.x|5.7.x|
  |------|-----|-----|-----|-----|-----|-----|-----|
  |5.0   |5.1  |5.2  |5.3  |5.4  |5.5  |5.6  |5.7  |
  |5.0.1 |5.1.1|5.2.1|5.3.1|5.4.1|5.5.1|5.6.1|
  |5.0.2 |5.1.2|5.2.2|5.3.2|5.4.2|5.5.2|5.6.2|
  |5.0.3 |5.1.3|5.2.3|5.3.3|5.4.3|5.5.3|
  |5.0.4 |5.1.4|5.2.4|5.3.4|5.4.4|
  |5.0.5 |5.1.5|5.2.5|5.3.5|
  |5.0.6 |5.1.6|5.2.6|5.3.6|
  |5.0.7 |5.1.7|5.2.7|
  |5.0.8 |5.1.8|5.2.8|
  |5.0.9 |     |5.2.9|
  |5.0.10|
  |5.0.11|

</details>

or

```
latest
```

## Usage

First create a `mysql` container with user root and no password

```
docker run --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=true -d mysql:5
```

and then you can run:

```
docker run --rm -v $(pwd):/opt --link mysql frozzare/wptest:7.0 vendor/bin/phpunit
```

If you run it on Windows and get error like `... "$(pwd)" includes invalid characters...`, try to use `%cd%` (in Windows Command Line) instead of `$(pwd)`:

```
docker run --rm -v %cd%:/opt --link mysql frozzare/wptest:7.0 vendor/bin/phpunit
```

or `${PWD}` (in PowerShell):

```
docker run --rm -v ${PWD}:/opt --link mysql frozzare/wptest:7.0 vendor/bin/phpunit
```

If you would like to test against another WordPress version add the environment variable `WP_VERSION=4.4` when you run the container.

## Contributing

Add new WordPress versions to `versions.sh` and run `update.sh` instead of adding them to each docker container and update the readme file with new versions.

## License

MIT © [Fredrik Forsmo](https://github.com/frozzare)
