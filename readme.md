### Laravel Development Containers for Visual Studio Code

`laravel-devcontainer` is a simple configuration to support fully-dockerised development of Laravel applications using Visual Studio Code.
Unlike Laravel Sail, `laravel-devcontainer` has been built so that the entire development experience is dockerised. The only requirements are:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Visual Studio Code Remote Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

Visual Studio Code will actually run inside a Docker container with php-cli as well as other development tools.
Any Extensions will also run in the same container, meaning that intellisense will use the same php-cli configuration!

`laravel-devcontainer` currently ships with:

- `php:8.3-cli-alpine` workspace with composer, pgsql, redis, and nodejs.
- `php:8.3-fpm-alpine` container with pgsql and redis extensions.
- `nginx:1.27-alpine` preconfigured for your Laravel application.
- `postgres:16.3-alpine` preconfigured with the default Laravel credentials.
- `redis:7.2-alpine` for caching, queues, sessions, etc.

#### Easy Installation

Using this configuration is quite simple. [Download](https://github.com/theomessin/laravel-devcontainer/archive/refs/heads/master.zip) and place `laravel-devcontainer` in a `.devcontainer` folder with your Laravel Code. If starting a new project, you may create a new folder with just `laravel-devcontainer` in your `.devcontainer` folder. You may then [install Laravel using Composer](https://laravel.com/docs/11.x/installation#creating-a-laravel-project) (e.g. under `example-app`). You may then move the `.devcontainer` folder to your code folder (`mv .devcontainer example-app`) and use that!

#### Installing Using Git Submodules

Alternatively, you may use [Git Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules). Install the configuration by running

```sh
git submodule add https://github.com/theomessin/laravel-devcontainer .devcontainer
```

If you use this method, do not forget to install submodules when cloning:

```
git clone --recurse-submodules ...
```

#### Usage

Start Visual Studio Code (e.g. `code example-app`) and re-open in remote containers (`Remote-Containers: Reopen in Container`). This may take some time on the first use, as Docker initially downloads and builds the images. Eventually, Visual Studio Code will run inside the workspace container. Extensions and settings specified in `devcontainer.json` will be auto-configured!

Be sure to correctly configure your application `.env` to use the devcontainer postgres and redis. For example:

```env
DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```

You may then navigate to [`localhost`](http://localhost) on your local machine. Fingers crossed, you will see your Laravel application!
Run any artisan or composer commands using the Visual Studio Code [Integrated Terminal](https://code.visualstudio.com/docs/editor/integrated-terminal).
As such, you do not need anything else installed on your host machine!

#### Extensions

`laravel-devcontainer` currently ships with the following extensions for Laravel development in Visual Studio Code:

- ["bmewburn.vscode-intelephense-client"](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)
- ["eamodio.gitlens"](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- ["EditorConfig.EditorConfig"](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- ["mikestead.dotenv"](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- ["onecentlin.laravel-blade"](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade)
