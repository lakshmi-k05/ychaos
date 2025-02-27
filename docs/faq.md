# FAQ (Frequently Asked questions)

## I have no idea why I am here!

Great! You can start with YChaos [here](index.md)

## I am a YChaos user

#### What version of YChaos should I install?

It is always recommended to install the latest version(PATCH) of YChaos for
the chaos testing. Although we test the package thoroughly for each PATCH
update, there might be unknown regressions/bugs introduced in the new PATCH versions.
To avoid this, you can install the latest MINOR version.

## I am a YChaos Contributor

#### I do not like the way something is coded in this package. How do I bring the attention of this to the maintainers?

Its not wrong to design things better than they are right now. Create a Github issue
explaining what you do not like and how you would change it. If the change
is approved, you can always contribute to the repository. We would likely
not make this change to the repo.

This is the same for suggesting adding a new feature to YChaos. Discuss and contribute.
In the case of new features, we might actually contribute if its worthwhile.

#### How do I add a new optional 3rd party package to the tool.

Discuss the usecase you are trying to solve by creating a Github issue with us.
Once approved to add new package to the repository, add the package at the right place
in `setup.cfg`.

`install_requires` are the list of PyPi packages that are installed by default.
`options.extras_require` are the optional dependencies that contains subpackages
and also dev packages.

#### How do I run a single Unittest from command line?

We recommend you to use an IDE for development. (Preferably PyCharm)
which will provide you the feature of running a single unittest suite or a single test
out of the box. If you still like to run it via command line you can use the below command.

```bash
pytest <TEST_SUITE> -k "<TEST_NAME>"
```

For example, 

```bash
pytest tests/test_settings.py -k "test_settings_with_no_config_creates_ProdSettings_configuration"
```


## I am a YChaos Maintainer

#### When do I need to release new minor versions?

1. New subcommand is added to YChaos CLI *
2. Backward incompatible testplan
3. New Verification Plugin *
4. New YChaos Agent *
5. Backward incompatible CLI changes (Arguments etc.)

For the items marked with *, the PR with the changes can go in first
and a new patch release can be released. After that, the package can be
bumped to new minor version.

For the items without *, the changes and the new version should go in
as a same release. A patch version with this update should not be released.

#### How do I release a backward incompatible YChaos Testplan?

Its always ideal to keep the testplan backward compatible as much as possible.
This may not possible based on the new usecases coming in.
All the changes that break the current setup should be part of one Pull
Request. The PR owner should also update the minor version of the package
in this PR. A new minor version should be released upon merging this PR.

#### Do I need to release all the commits as a new patch version?

Yes. This is part of the repository pipeline and this behaviour should not
be changed. Every single commit, should automatically release a new version
of the package.
