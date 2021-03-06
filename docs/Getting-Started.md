# Getting Started

<html>
<img src="/img/runner_start.svg" style="height: 300px; width: 100%; ">
</html>
<br>
<br>

Getting started with TerrabaseDB is easy 😊 (and fun!). You can get started with [native binaries (recommended)](#get-started-with-bundles) or by using the [docker image](#get-started-with-docker).

## Get started with bundles

### Step 1: Download a bundle

Head over to the [releases page](https://github.com/terrabasedb/terrabase/releases) and download the latest version for your platform. Here's a little guide:

* If you're on Linux: Download `tdb-bundle-<version>-x86_64-linux-gnu.zip`
* If you're using macOS: Download `tdb-bundle-<version>-x86_64-macos.zip`
* If you're on Windows: Download `tdb-bundle-<version>-x86_64-windows.zip`

### Step 2: Make the files runnable

Unzip the `zip` file that you just downloaded. If you're on a *nix system, run `chmod +x tdb tsh` to make the files executable. If you're on Windows, right-click the files and then check the `UNBLOCK` checkbox and click on the `APPLY` button.

### Step 3: Start the database server

In the directory where you extracted the files, run `./tdb` on *nix systems or simply `tdb` on Windows systems. That's all there is to starting the database server!

### Step 4: Run the shell `tsh`

`tsh` is the shell that is shipped with the bundle. Run it, just like you did with the database server. Now enter commands in the shell, and have fun! First run `HEYA` to check if everything is fine - the server should reply with _HEY!_.
See all the available actions [here](/List-Of-Actions)

You're done with setting up `tdb` 🎉!

## Get started with Docker

First of all, you need to have Docker installed and available on your `PATH` ; you can read the official guide [here](https://docs.docker.com/get-docker/). Once you've got Docker up and running, follow the steps!

### Step 0: Create a container

Open up a terminal and run:

``` 
docker create terrabasedb/tdb --name tdbvm
```

> **NOTE:** You may need superuser priveleges

At the same time, you'll need to set up the bundle by following [Step 1](#step-1-download-a-bundle) and [Step 2](#step-2-make-the-files-runnable) from the previous section.

### Step 1: Start the container

Now run:

``` 
docker start tdbvm
```

> **NOTE:** You may need superuser priveleges

### Step 2: Find the IP address of the container

In order to connect to the container (which, to `tsh` is nothing but a remote server), you'll have to run:

``` shell
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' tdbvm
```

> **NOTE:** You may need superuser priveleges

And you'll get a result like:

``` text
172.17.0.1
```

### Step 3: Start the command line client

Open up a terminal in the directory where you downloaded the command line client and run:

``` shell
tsh -h 172.17.0.1
```

And you're done!
