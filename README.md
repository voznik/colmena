![](apps/admin/src/assets/logo.png?raw=true)

***

<h3 align="center">

``` javascript
Free + Full Stack + Open Source + Rapid API Development
```

</h3>

<p align="center" class="mb-0">
  <a href="#contributors"><img src="https://img.shields.io/badge/all_contributors-26-orange.svg?style=flat-square" /></a>
  <a href="https://colmena-slack.now.sh/"><img src="https://colmena-slack.now.sh/badge.svg" /></a>
  <a href="#backers"><img src="https://opencollective.com/colmena/backers/badge.svg" /></a>
  <a href="#sponsors"><img src="https://opencollective.com/colmena/sponsors/badge.svg" /></a>
</p>

#

>> powered by [LoopBack](https://loopback.io/) and [Angular](https://angular.io/)
>>> This project was formerly known as [Loopback Angular Admin](https://github.com/beeman/loopback-angular-admin).

## About

Colmena is a starter kit for an API with an Admin interface that can be easily extended and built upon.

It is built using a collection of great Open Source projects, including but not limited to:

- [LoopBack](https://loopback.io/) - API server based on Express.
- [Angular](https://angular.io/) - MVC framework to build web apps.
- [LoopBack SDK Builder](https://www.npmjs.com/package/@mean-expert/loopback-sdk-builder) - Awesome integration of Loopback and Angular.
- [CoreUI](http://coreui.io/) - Amazing Bootstrap Admin Template.

## ⚠️ Warning

#### This software is under active development!
#### Please do not use it in production without addressing the issues in the [Work in Progress](#work-in-progress) section


## Work in Progress

Colmena is a work in progress and not all functionality is built yet.

- Only basic ACLS are implemented, this means that the API can be used by whoever has access to it
- The interface does not reflect the user role (admin/manager/user)
- Content will be leaking across domains, while this should not be possible

## Structure

The project is a mono-repo managed by [lerna](https://lernajs.io). It is structured like this:

- `apps/`
  - `admin` The Admin interface built with Angular.
  - `api` The REST API built with LoopBack.
- `modules/`
  - `admin-*` Modules that add functionality to the Admin app.
  - `api-*` Modules that add functionality to the API app.
- `packages/`
  - `admin-*` Packages used by the Admin app.
  - `api-*` Packages used by the API app.

The structure of this project is inspired by this great example: [OasisDigital/scalable-enterprise-angular](https://github.com/OasisDigital/scalable-enterprise-angular).

## Installation

### Requirements

#### Software installed on your system:

- `node` (v6.9.x or higher).
- `npm` (v3.x or higher).


#### Globally installed Node packages:

- [Angular CLI](https://github.com/angular/angular-cli)
- [Lerna](https://github.com/lerna/lerna)
- [LoopBack CLI](https://github.com/strongloop/loopback-cli)

```bash
npm install -g @angular/cli lerna loopback-cli
```

### Setup

Clone the repository and install the dependencies:

```bash
git clone https://github.com/colmena/colmena
cd colmena
npm install
```


## Development

### Running in development mode

When the project is running in development mode the API and the Admin will restart automatically when a code change is
detected.

#### URLs
- The API listens on [http://127.0.0.1:3000](http://127.0.0.1:3000).
- The Admin listens on [http://127.0.0.1:9000](http://127.0.0.1:9000).

#### Start the project

From inside the project dir run `npm run dev`:

```bash
npm run dev
```

This will start both the API and the Admin in the same terminal.

You can also start the two components separately:

#### Start the API

```bash
npm run dev:api
```

#### Start the Admin

```bash
npm run dev:admin
```

#### Clean up the project

During development it can be useful to bring the project back to a clean state. To do this run:

```bash
npm run clean && npm install
```

### Configuring the development setup

#### local.yaml

You can configure the API in development mode by creating a `local.yaml` file in `apps/api/config`. The contents of this
file is not tracked by git so it only lives on your local machine.

To start with the default settings copy `apps/api/config/default.yaml` to `apps/api/config/local.yaml`.


#### Sample data

The API comes with a set of sample data for development.

To load the sample data when starting the API update [`local.yaml`](#localyaml) to include:

```yaml
system:
  initdb: true
```

You can also use the `INITDB` environment variable.

#### API Base Url

By default the development stack assumes that the API and Admin are both started on localhost (using `127.0.0.1`).

In order to run the API on another host than localhost the admin needs to know on which IP address it can reach the API. 
To do this you need to update the `api.baseUrl` config property.

> Make sure to configure the API Base Url **without** a trailing slash.

To set the API Base Url update [`local.yaml`](#localyaml) to include:

```yaml
api:
  # Do not use trailing spaces for the baseUrl
  baseUrl: http://192.168.12.34:3000
```

You can also use the `API_BASE_URL` environment variable.

You should now be able to connect to the Admin on http://192.168.12.34:9000 and it should connect to the API.


### Development Servers

Colmena comes with a Docker Compose configuration for running development servers easily.

#### mongodb

To use the mongodb server update [`local.yaml`](#localyaml) to include:

```yaml
mongodb:
  url: mongodb://localhost/colmena
```

You can also use the `MONGODB_URL` environment variable

#### mailhog

To use the mailhog server update [`local.yaml`](#localyaml) to include:

```yaml
smtp:
  host: localhost
  port: 1025
```

You can also use the `SMTP_HOST` and `SMTP_PORT` environment variables

#### Start the servers

```bash
npm run servers # or: npm run servers:start
```

#### Show the servers logging

```bash
npm run servers:logs
```

#### Stop the servers

```bash
npm run servers:stop
```

#### Delete the servers

```bash
npm run servers:rm
```

## Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
| [<img src="https://avatars.githubusercontent.com/u/36491?v=3" width="100px;"/><br /><sub>Bram Borggreve</sub>](http://colmena.io/)<br />[💬](#question-beeman "Answering Questions") [🐛](https://github.com/colmena/colmena/issues?q=author%3Abeeman "Bug reports") [💻](https://github.com/colmena/colmena/commits?author=beeman "Code") [🎨](#design-beeman "Design") [📖](https://github.com/colmena/colmena/commits?author=beeman "Documentation") [🔧](#tool-beeman "Tools") | [<img src="https://avatars.githubusercontent.com/u/1755489?v=3" width="100px;"/><br /><sub>Willian Ribeiro Angelo</sub>](https://github.com/movibe)<br />[💻](https://github.com/colmena/colmena/commits?author=movibe "Code") | [<img src="https://avatars.githubusercontent.com/u/977025?v=3" width="100px;"/><br /><sub>Nick Portokallidis</sub>](http://nporto.com)<br />[💻](https://github.com/colmena/colmena/commits?author=portokallidis "Code") | [<img src="https://avatars.githubusercontent.com/u/90312?v=3" width="100px;"/><br /><sub>drmikecrowe</sub>](https://github.com/drmikecrowe)<br />[💻](https://github.com/colmena/colmena/commits?author=drmikecrowe "Code") | [<img src="https://avatars.githubusercontent.com/u/1899626?v=3" width="100px;"/><br /><sub>Vladimir Mechkauskas</sub>](http://elartix.com/)<br />[💻](https://github.com/colmena/colmena/commits?author=elartix "Code") | [<img src="https://avatars.githubusercontent.com/u/4164460?v=3" width="100px;"/><br /><sub>Bernardo Arevalo</sub>](https://github.com/nardoguy14)<br />[💻](https://github.com/colmena/colmena/commits?author=nardoguy14 "Code") | [<img src="https://avatars.githubusercontent.com/u/8195533?v=3" width="100px;"/><br /><sub>yieme</sub>](https://github.com/yieme)<br />[💻](https://github.com/colmena/colmena/commits?author=yieme "Code") |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| [<img src="https://avatars.githubusercontent.com/u/339169?v=3" width="100px;"/><br /><sub>Brian McIntyre</sub>](https://github.com/bmcintyre)<br />[💻](https://github.com/colmena/colmena/commits?author=bmcintyre "Code") | [<img src="https://avatars.githubusercontent.com/u/274358?v=3" width="100px;"/><br /><sub>Rob Halff</sub>](https://github.com/rhalff)<br />[💻](https://github.com/colmena/colmena/commits?author=rhalff "Code") | [<img src="https://avatars.githubusercontent.com/u/3543429?v=3" width="100px;"/><br /><sub>Asgeir Birkisson</sub>](https://github.com/asgeirbirkis)<br />[💻](https://github.com/colmena/colmena/commits?author=asgeirbirkis "Code") | [<img src="https://avatars.githubusercontent.com/u/6855743?v=3" width="100px;"/><br /><sub>dthib</sub>](https://github.com/dthib)<br />[💻](https://github.com/colmena/colmena/commits?author=dthib "Code") | [<img src="https://avatars.githubusercontent.com/u/3319777?v=3" width="100px;"/><br /><sub>Oleh Kukil</sub>](http://brainstorage.me/flashbag)<br />[💻](https://github.com/colmena/colmena/commits?author=flashbag "Code") | [<img src="https://avatars.githubusercontent.com/u/821963?v=3" width="100px;"/><br /><sub>Pulkit Singhal</sub>](http://pulkitsinghal.blogspot.com)<br />[💻](https://github.com/colmena/colmena/commits?author=pulkitsinghal "Code") | [<img src="https://avatars.githubusercontent.com/u/1904924?v=3" width="100px;"/><br /><sub>Tuan PM</sub>](http://tuanpm.net)<br />[💻](https://github.com/colmena/colmena/commits?author=tuanpmt "Code") |
| [<img src="https://avatars.githubusercontent.com/u/314539?v=3" width="100px;"/><br /><sub>brownman</sub>](http://brownman.github.io)<br />[💻](https://github.com/colmena/colmena/commits?author=brownman "Code") | [<img src="https://avatars.githubusercontent.com/u/8570291?v=3" width="100px;"/><br /><sub>Hoàng Phúc</sub>](https://github.com/hoangtrongphuc)<br />[💻](https://github.com/colmena/colmena/commits?author=hoangtrongphuc "Code") | [<img src="https://avatars.githubusercontent.com/u/175838?v=3" width="100px;"/><br /><sub>Brian Dunnette</sub>](http://brian.dunnette.us)<br />[💻](https://github.com/colmena/colmena/commits?author=bdunnette "Code") | [<img src="https://avatars.githubusercontent.com/u/4792828?v=3" width="100px;"/><br /><sub>Chenzc</sub>](https://github.com/Chenzc)<br />[💻](https://github.com/colmena/colmena/commits?author=Chenzc "Code") | [<img src="https://avatars.githubusercontent.com/u/6417718?v=3" width="100px;"/><br /><sub>Tersius Kuhne</sub>](https://github.com/ktersius)<br />[💻](https://github.com/colmena/colmena/commits?author=ktersius "Code") | [<img src="https://avatars.githubusercontent.com/u/1888261?v=3" width="100px;"/><br /><sub>Alex Quiambao</sub>](https://github.com/silverbux)<br />[💻](https://github.com/colmena/colmena/commits?author=silverbux "Code") | [<img src="https://avatars.githubusercontent.com/u/791137?v=3" width="100px;"/><br /><sub>José Luis Di Biase</sub>](http://www.camba.coop)<br />[💻](https://github.com/colmena/colmena/commits?author=josx "Code") |
| [<img src="https://avatars.githubusercontent.com/u/5630513?v=3" width="100px;"/><br /><sub>Shing.</sub>](https://github.com/yshing)<br />[💻](https://github.com/colmena/colmena/commits?author=yshing "Code") | [<img src="https://avatars.githubusercontent.com/u/67973?v=3" width="100px;"/><br /><sub>Alex Wilde</sub>](alexthewilde.github.io)<br />[💻](https://github.com/colmena/colmena/commits?author=alexthewilde "Code") | [<img src="https://avatars.githubusercontent.com/u/529030?v=3" width="100px;"/><br /><sub>dmtw</sub>](https://github.com/dmtw)<br />[💻](https://github.com/colmena/colmena/commits?author=dmtw "Code") | [<img src="https://avatars3.githubusercontent.com/u/5523938?v=3" width="100px;"/><br /><sub>Marcus</sub>](https://github.com/kumorig)<br />[💻](https://github.com/colmena/colmena/commits?author=kumorig "Code") | [<img src="https://avatars2.githubusercontent.com/u/6089253?v=3" width="100px;"/><br /><sub>Brannon N. Darby II</sub>](https://github.com/brannon-darby)<br />[💻](https://github.com/colmena/colmena/commits?author=brannon-darby "Code") |
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification. Contributions of any kind welcome!

## Backers

Support us with a monthly donation and help us continue our activities. [[Become a backer](https://opencollective.com/colmena#backer)]

<a href="https://opencollective.com/colmena/backer/0/website" target="_blank"><img src="https://opencollective.com/colmena/backer/0/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/1/website" target="_blank"><img src="https://opencollective.com/colmena/backer/1/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/2/website" target="_blank"><img src="https://opencollective.com/colmena/backer/2/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/3/website" target="_blank"><img src="https://opencollective.com/colmena/backer/3/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/4/website" target="_blank"><img src="https://opencollective.com/colmena/backer/4/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/5/website" target="_blank"><img src="https://opencollective.com/colmena/backer/5/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/6/website" target="_blank"><img src="https://opencollective.com/colmena/backer/6/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/7/website" target="_blank"><img src="https://opencollective.com/colmena/backer/7/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/8/website" target="_blank"><img src="https://opencollective.com/colmena/backer/8/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/9/website" target="_blank"><img src="https://opencollective.com/colmena/backer/9/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/10/website" target="_blank"><img src="https://opencollective.com/colmena/backer/10/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/11/website" target="_blank"><img src="https://opencollective.com/colmena/backer/11/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/12/website" target="_blank"><img src="https://opencollective.com/colmena/backer/12/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/13/website" target="_blank"><img src="https://opencollective.com/colmena/backer/13/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/14/website" target="_blank"><img src="https://opencollective.com/colmena/backer/14/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/15/website" target="_blank"><img src="https://opencollective.com/colmena/backer/15/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/16/website" target="_blank"><img src="https://opencollective.com/colmena/backer/16/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/17/website" target="_blank"><img src="https://opencollective.com/colmena/backer/17/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/18/website" target="_blank"><img src="https://opencollective.com/colmena/backer/18/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/19/website" target="_blank"><img src="https://opencollective.com/colmena/backer/19/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/20/website" target="_blank"><img src="https://opencollective.com/colmena/backer/20/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/21/website" target="_blank"><img src="https://opencollective.com/colmena/backer/21/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/22/website" target="_blank"><img src="https://opencollective.com/colmena/backer/22/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/23/website" target="_blank"><img src="https://opencollective.com/colmena/backer/23/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/24/website" target="_blank"><img src="https://opencollective.com/colmena/backer/24/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/25/website" target="_blank"><img src="https://opencollective.com/colmena/backer/25/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/26/website" target="_blank"><img src="https://opencollective.com/colmena/backer/26/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/27/website" target="_blank"><img src="https://opencollective.com/colmena/backer/27/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/28/website" target="_blank"><img src="https://opencollective.com/colmena/backer/28/avatar.svg"></a>
<a href="https://opencollective.com/colmena/backer/29/website" target="_blank"><img src="https://opencollective.com/colmena/backer/29/avatar.svg"></a>


## Sponsors

Become a sponsor and get your logo on our README on Github with a link to your site. [[Become a sponsor](https://opencollective.com/colmena#sponsor)]

<a href="https://opencollective.com/colmena/sponsor/0/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/1/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/2/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/3/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/4/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/5/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/6/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/7/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/8/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/9/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/9/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/10/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/10/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/11/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/11/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/12/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/12/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/13/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/13/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/14/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/14/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/15/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/15/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/16/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/16/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/17/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/17/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/18/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/18/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/19/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/19/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/20/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/20/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/21/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/21/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/22/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/22/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/23/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/23/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/24/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/24/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/25/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/25/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/26/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/26/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/27/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/27/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/28/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/28/avatar.svg"></a>
<a href="https://opencollective.com/colmena/sponsor/29/website" target="_blank"><img src="https://opencollective.com/colmena/sponsor/29/avatar.svg"></a>
