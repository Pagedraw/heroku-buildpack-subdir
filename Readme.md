# STATUS: DEPRECATED AND UNMAINTAINED
This package is deprecated. Please use https://github.com/timanovsky/subdir-heroku-buildpack or https://github.com/lstoll/heroku-buildpack-monorepo.

# Heroku Buildpack Select Subdir

Allows you to have a monolithic repo with multiple Heroku apps in different subdirectories (like Google!).

## Usage

* Write a bunch of Procfiles and scatter them throughout your code base.
* Create a bunch of Heroku apps.
* For each app do `heroku buildpacks:set -a <app> https://github.com/Pagedraw/heroku-buildpack-select-subdir`
* For each app, specify a `<subdir>` and a buildpack by setting
```heroku config:add BUILDPACK='<subdir>=https://github.com/desired/heroku-buildpack' -a <app>```
* For each app, `git push git@heroku.com:<app> master`

This buildpack assumes each subdirectory added above has a Procfile in it. It will

1. Run each app's specified buildpack at the corresponding subdirectory
2. Copy the Procfile found at the specified subdirectory to the root
3. Source all files added to the `.profile.d/` directory by the buildpack from 1.

This means each Procfile must contain something like
```web: cd <subdir> && npm start```


## License

MIT
