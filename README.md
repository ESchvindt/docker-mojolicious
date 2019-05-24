<!-- this file is generated via docker-builder/generate.pl, do not edit it directly -->

# What is Mojolicious?

[Mojolicious](https://mojolicious.org) is a real-time web framework and web development toolkit written
in [Perl](https://www.perl.org).

The images are based on perl:5.28.2 and provide Mojolicious installed together with
[Cpanel::JSON::XS](https://metacpan.org/pod/Cpanel::JSON::XS),
[DBI](https://metacpan.org/pod/DBI),
[EV](https://metacpan.org/pod/EV),
[IO::Socket::Socks](https://metacpan.org/pod/IO::Socket::Socks),
[IO::Socket::SSL](https://metacpan.org/pod/IO::Socket::SSL),
[Net::DNS::Native](https://metacpan.org/pod/Net::DNS::Native),
[Role::Tiny](https://metacpan.org/pod/Role::Tiny) and
[SQL::Abstract](https://metacpan.org/pod/SQL::Abstract).

# Supported tags and respective Dockerfile links

* Mojolicious: [8.17, 8, latest (main/Dockerfile)](https://github.com/Tekki/docker-mojolicious/blob/master/main/Dockerfile)

* Mojolicious with Mojo::mysql and the MariaDB libraries: [8.17-mariadb, 8-mariadb, mariadb (mariadb/Dockerfile)](https://github.com/Tekki/docker-mojolicious/blob/master/mariadb/Dockerfile)

* Mojolicious with Mojo::mysql and the MySQL libraries: [8.17-mysql, 8-mysql, mysql (mysql/Dockerfile)](https://github.com/Tekki/docker-mojolicious/blob/master/mysql/Dockerfile)

* Mojolicious with Mojo::Pg: [8.17-pg, 8-pg, pg (pg/Dockerfile)](https://github.com/Tekki/docker-mojolicious/blob/master/pg/Dockerfile)

* Mojolicious with Mojo::SQLite: [8.17-sqlite, 8-sqlite, sqlite (sqlite/Dockerfile)](https://github.com/Tekki/docker-mojolicious/blob/master/sqlite/Dockerfile)

`mariadb` and `mysql` both include DBD::MariaDB and DBD::mysql. The difference is
in the C libraries they are built with.

# How to use this image

## Simple application

Go to your code folder, call Mojolicious to create the basic application structure.

    $ docker run --rm -v "$(pwd):/usr/src/app" tekki/mojolicious mojo generate app MyApp

Start the application as daemon.

    $ cd my_app
    $ docker run -d --rm -v "$(pwd):/usr/src/app" -p 3000:3000 tekki/mojolicious morbo script/my_app

To run the container in the foreground and read the output, omit the `-d`.
Browse to [localhost:3000](http://localhost:3000) and edit the code in the current folder.
If you are on Linux or MacOS, the server will restart whenever you change a file.
If you are on Windows, guess what...

The application inside the container always has to run in the foreground. For hypnotoad use the `-f` flag.

    $ docker run -d --rm -v "$(pwd):/usr/src/app" -p 8080:8080 tekki/mojolicious hypnotoad -f script/my_app
