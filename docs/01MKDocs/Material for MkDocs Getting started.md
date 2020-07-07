# Material for MkDocs Getting started

## Installation

While there are several ways of installing Material for MkDocs, the recommended
methods are either by using `pip` – the Python package manager – or by pulling
the [official Docker image][1].


!!! tip "Installation in a virtual environment"

    The best way to make sure that you end up with the correct versions and
    without any incompatibility problems between packages it to use a **virtual
    environment**. Don't know what this is or how to set it up? We recommend
    to start by reading a [tutorial on virtual environments][6] for Python.

!!! warning "Installation on macOS"

    When you're running the pre-installed version of Python on macOS, `pip`
    tries to install packages in a folder for which your user might not have
    the adequate permissions. There are two possible solutions for this:
    
    1. **Installing in user space** (recommended): Provide the `--user` flag
      to the install command and `pip` will install the package in a user-site
      location. This is the recommended way.
    
    2. **Switching to a homebrewed Python**: Upgrade your Python installation
      to a self-contained solution by installing Python with Homebrew. This
      should eliminate a lot of problems you could be having with `pip`.

!!! failure "Error: unrecognized theme 'material'"

    If you run into this error, the most common reason is that you installed
    MkDocs through some package manager (e.g. Homebrew or `apt-get`) and
    Material for MkDocs through `pip`, so both packages end up in different
    locations. MkDocs only checks its install location for themes.

[2]: https://www.mkdocs.org
[3]: https://python-markdown.github.io/
[4]: https://pygments.org/
[5]: https://facelessuser.github.io/pymdown-extensions/
[6]: https://docs.python-guide.org/dev/virtualenvs/



### with docker <small>recommended</small>

The official [Docker image][7] is a great way to get up and running in a few
minutes, as it comes with all dependencies pre-installed. Pull the image for the 
`latest` version with:

```
docker pull squidfunk/mkdocs-material
```

The `mkdocs` executable is provided as an entry point and `serve` is the default
command. Start the development server in your project root – the folder where
`mkdocs.yml` resides — with:

=== "Unix"

    ```
    docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
    ```

=== "Windows"

    ```
    docker run --rm -it -p 8000:8000 -v "%cd%":/docs squidfunk/mkdocs-material
    ```

[7]: https://hub.docker.com/r/squidfunk/mkdocs-material/

### with git

Material for MkDocs can be directly used from [GitHub][8] by cloning the
repository into a subfolder of your project root which might be useful if you
want to use the very latest version:

``` sh
git clone https://github.com/squidfunk/mkdocs-material.git
```

The theme will reside in the folder `mkdocs-material/material`.

[8]: https://github.com/squidfunk/mkdocs-material

## Configuration

Depending on your ==installation== method, you can now add the following lines to
`mkdocs.yml` in your project root. If you installed Material for MkDocs using
a package manager, add:

``` yaml
theme:
  name: material
```

If you cloned Material for MkDocs from GitHub add:

``` yaml
theme:
  name: null
  custom_dir: mkdocs-material/material
```

MkDocs includes a development server, so you can preview your changes as you
write your documentation. The development server can be started with the
following command:

``` sh
mkdocs serve
```

Point your browser to http://localhost:8000 and your documentation should greet
you in a new look. If you're starting from scratch, the following configuration
can be used as a starting point:


??? summary "Example configuration"

    This is an excerpt from the [`mkdocs.yml`][9] used to render these pages:
    
    ``` yaml
    # Project information
    site_name: Material for MkDocs
    site_description: A Material Design theme for MkDocs
    site_author: Martin Donath
    site_url: https://squidfunk.github.io/mkdocs-material/
    
    # Repository
    repo_name: squidfunk/mkdocs-material
    repo_url: https://github.com/squidfunk/mkdocs-material
    
    # Copyright
    copyright: Copyright &copy; 2016 - 2020 Martin Donath
    
    # Configuration
    theme:
      name: material
      language: en
      palette:
        primary: indigo
        accent: indigo
      font:
        text: Roboto
        code: Roboto Mono
    
    # Extras
    extra:
      social:
        - icon: fontawesome/brands/github-alt
          link: https://github.com/squidfunk
        - icon: fontawesome/brands/twitter
          link: https://twitter.com/squidfunk
        - icon: fontawesome/brands/linkedin
          link: https://linkedin.com/in/squidfunk
    
    # Google Analytics
    google_analytics:
      - UA-XXXXXXXX-X
      - auto
    
    # Extensions
    markdown_extensions:
      - admonition
      - codehilite:
          guess_lang: false
      - toc:
          permalink: true
    ```