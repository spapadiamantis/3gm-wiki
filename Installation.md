# Installation

This page will guide you through the installation process using a [the provided Makefile](https://github.com/eellak/gsoc2018-3gm/blob/master/Makefile). You can build various modules of the project using this Makefile. We chose to use GNU Make because the project is not vanilla Python and `make` is [target-agnostic](https://whatis.techtarget.com/definition/agnostic). 

## Installing main module (core functionality)

To install the main module including:

1.  Core modules
2. MongoDB Integration
3. Web Application
4. NLP Toolkit

use the following command:

```bash
make core
```

If you want to build the full codifier pipeline:

Export the `CODIFIER_DATA` environment variable:

```bash
export CODIFIER_DATA=/home/to/codifier/texts
```

And run `make`:

```bash
make codifier_pipeline
```

If you want to run the web application:

```bash
make run_web_application
```

## Installing scripts

Installing the scripts includes:

1. Tesseract 4.0
2. pyocr
3. pdfminer.six
4. Chromedriver w. selenium

To install the scripts: 

```bash
make scripts
```

To schedule cron jobs:

```bash
make schedule_cronjobs
```

If you want to install both (core and scripts) you can type:

```bash
make all
```

