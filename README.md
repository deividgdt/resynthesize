REsynthesize
==========
[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U7U01LTQB)

:exclamation: `REsynthesize` is a fork of `synthesize`. This script only works for CentOS distributions (8.1 and older). For Ubuntu, refer to [synthesize](https://github.com/obfuscurity/synthesize)

Installing Graphite doesn't have to be difficult. The `resynthesize` script in synthesize is designed to make it brain-dead easy to install Graphite and related services onto a modern Linux distribution.

RESynthesize is built to run on CentOS 8.1 and older. It will __not__ run on other Linux distributions. The goal of this project is not to become an automation alternative to modern configuration management utilities (e.g. Chef or Puppet), but rather, to make it as easy as possible for the beginner Graphite user to get started and familiar with the project without having to learn a suite of other automation and/or infrastructure-related projects.

The resulting Graphite web interface __listens only on https port 443__ and has been configured to collect metrics specifically for helping profile the performance of your Graphite and Carbon services. It uses memcached for improved query performance, and Statsite for a fast, C-based implementation of the StatsD collector/aggregator.

Beginning with version 3.0.0 we've also incorporated the Grafana dashboard project, a modern and full-featured alternative to Graphite's built-in Composer and Dashboard interfaces. It also includes a default dashboard for monitoring Carbon's internal statistics.

:warning: **WARNING:** You should not install REsynthesize directly on your personal development system. It's strongly suggested that you use a VM or other temporary VPS instance for sandboxing REsynthesize.

## Provides

* Graphite 1.1.7 ([graphite-web](https://github.com/graphite-project/graphite-web), [carbon](https://github.com/graphite-project/carbon), [whisper](https://github.com/graphite-project/whisper))
* StatsD ([statsite](https://github.com/armon/statsite))
* [Collectd](http://collectd.org/)
* [Grafana](https://grafana.org/)

## Dependencies

* CentOS 8.1 and older

## Installation


```
$ git clone https://github.com/deividgdt/resynthesize
$ cd resynthesize
$ sudo ./resynthesize -i
```

## Administration

### Graphite-Web

There is a superuser (Django) account that grants access to the administrative features in the backend Django database. The default credentials are:

* username `admin`
* password `graphite_me_synthesize`

These credentials can be changed with the following commands:

```
$ cd /opt/graphite/webapp/graphite
$ sudo python manage.py changepassword admin
```

### Grafana

Grafana includes a default user to start:

* username `admin`
* password `admin`

## Upgrade

:warning: **WARNING:** The following information is outdated for this experimental branch. If you attempt to run the upgrade script it will display a warning with further instructions to acknowledge the current experimental status and override the warning.

It's now possible to upgrade an existing Synthesize (e.g. Graphite 0.9.15) to the newest Graphite `HEAD`. Besides upgrading the Graphite components, it will also migrate the webapp database (`graphite.db`) to the newest fixtures version.

```
$ cd resynthesize
$ sudo ./resynthesize -u
```

## Removal

### Manual

```
$ cd synthesize
$ sudo ./resynthesize -d
```

## License

REsynthesize is distributed under the MIT license.

