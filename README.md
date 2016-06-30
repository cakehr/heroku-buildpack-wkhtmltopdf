# wkhtmltopdf Buildpack

This is a [Heroku buildpack][0] for bundling a compatible [wkhtmltopdf][1] binary with your environment.

## Versions

* Buildpack:   `0.3`
* wkhtmltopdf: `0.12.3`

## Usage

This buildpack only installs wkhtmltopdf, it isn't very useful by itself. You'll probably want to use it as part of a multi-buildpack. Here is an example using the Ruby buildpack.

```bash
$ heroku buildpacks:set https://github.com/heroku/heroku-buildpack-ruby.git
$ heroku buildpacks:add https://github.com/dscout/wkhtmltopdf-buildpack.git
```

### Clearing Repo Cache

Remember to clean your repository cache if you are updating the version of buildpack. To do that, run:

```bash
$ heroku plugins:install https://github.com/heroku/heroku-repo.git
$ heroku repo:purge-cache -a appname
```

## Troubleshooting

If you run into issues when trying to deploy with this buildpack, make sure your app is running on Cedar with Ubuntu 14.04 (`cedar-14`). You can check this with:

```bash
$ heroku stack
```

If you are on an older stack, you can upgrade to `cedar-14` with:

```bash
$ heroku stack:set cedar-14
```

Note that wkhtmltopdf 0.12.3 depends on the following Debian/Ubuntu packages in
runtime:

- libfontconfig1
- libx11-6
- libxext6
- libxrender1

Fortunately, the `cedar-14` stack has all of those pre-installed.

[0]: http://devcenter.heroku.com/articles/buildpacks
[1]: http://wkhtmltopdf.org/
