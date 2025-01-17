# Serverless Benthos Project Skeleton

[![GitHub Actions](https://github.com/makenew/serverless-benthos/workflows/main/badge.svg)](https://github.com/makenew/serverless-benthos/actions)

Package skeleton for a Benthos Serverless project on AWS Lambda.

## Description

Bootstrap a new Benthos Serverless project in five minutes or less.

### Features

- Deploy [Benthos] to [AWS Lambda] with [Serverless].
- Unlimited, modular, and testable configs packaged with [Blobpack].
- [Node.js]'s [npm] package structure.
- [Prettier] code.
- Continuous testing and deployment with [GitHub Actions].
- [Keep a CHANGELOG].
- Consistent coding with [EditorConfig].

[Benthos]: https://www.benthos.dev/
[Blobpack]: https://github.com/razor-x/blobpack
[AWS Lambda]: https://aws.amazon.com/lambda/
[EditorConfig]: https://editorconfig.org/
[GitHub Actions]: https://github.com/features/actions
[Keep a CHANGELOG]: https://keepachangelog.com/
[Node.js]: https://nodejs.org/
[Prettier]: https://prettier.io/
[Serverless]: https://serverless.com/
[npm]: https://www.npmjs.com/

### Bootstrapping a new project

1. Create an empty (**non-initialized**) repository on GitHub.
2. Clone the master branch of this repository with
   ```
   $ git clone --single-branch git@github.com:makenew/serverless-benthos.git <new-benthos-app>
   $ cd <new-benthos-app>
   ```
   Optionally, reset to the latest version with
   ```
   $ git reset --hard <version-tag>
   ```
3. Run
   ```
   $ ./makenew.sh
   ```
   This will replace the boilerplate, delete itself,
   remove the git remote, remove upstream tags,
   and stage changes for commit.
4. Create the required GitHub repository secrets.
5. Review, commit, and push the changes to GitHub with
   ```
   $ git diff --cached
   $ git commit -m "Replace makenew boilerplate"
   $ git remote add origin git@github.com:<user>/<new-benthos-app>.git
   $ git push -u origin master
   ```
6. Ensure the GitHub action passes,
   then release the initial version with
   ```
   $ nvm install
   $ npm install
   $ npm version patch
   ```

### Updating from this skeleton

If you want to pull in future updates from this skeleton,
you can fetch and merge in changes from this repository.

Add this as a new remote with

```
$ git remote add upstream git@github.com:makenew/serverless-benthos.git
```

You can then fetch and merge changes with

```
$ git fetch --no-tags upstream
$ git merge upstream/master
```

#### Changelog for this skeleton

Note that `CHANGELOG.md` is just a template for this skeleton.
The actual changes for this project are documented in the commit history
and summarized under [Releases].

[Releases]: https://github.com/makenew/serverless-benthos/releases

## Development and Testing

### Quickstart

```
$ git clone https://github.com/makenew/serverless-benthos.git
$ cd serverless-benthos
$ nvm install
$ npm install
$ npm test
```

Primary development tasks are defined under `scripts` in `package.json`
and available via `npm run`.
View them with

```
$ npm run
```

### Source code

The [source code] is hosted on GitHub.
Clone the project with

```
$ git clone git@github.com:makenew/serverless-benthos.git
```

[source code]: https://github.com/makenew/serverless-benthos

### Requirements

You will need [Node.js] with [npm].
Optionally, to run tests you will need [Benthos].

Be sure that all commands run under the correct Node version, e.g.,
if using [nvm], install the correct version with

```
$ nvm install
```

Set the active version for each shell session with

```
$ nvm use
```

Install the development dependencies with

```
$ npm install
```

[Node.js]: https://nodejs.org/
[npm]: https://www.npmjs.com/
[nvm]: https://github.com/creationix/nvm

### Benthos Configuration and Testing

- Benthos configuration and unit tests live side-by-side in the `config` directory.
- Configuration is bundled with the deployed artifact
  to avoid the AWS environment variable 4K size limit.
- For each item in the `benthos.artifacts` array in `package.json`,
  a Serverless zip artifact will be built to `dist` containing
  the Benthos binary and the corresponding config.

#### Adding a new function

To add a new Serverless function nameed, e.g., `foo`:

1. Create `config/foo.yaml` and `config/foo_benthos_test.yaml`.
2. Update the `benthos.artifacts` array in `package.json` to include `foo`.
3. Set the new Serverless function's `package.artifact` to `dist/foo.zip`.

### Deployment

Serverless deployment is triggered by a release repository_dispatch on GitHub Actions.

Deployment may be triggered using on the web
using a [release workflow_dispatch on GitHub Actions].

[release workflow_dispatch on GitHub Actions]: https://github.com/makenew/serverless-benthos/actions?query=workflow%3Arelease

## GitHub Actions

_GitHub Actions should already be configured: this section is for reference only._

The following repository secrets must be set on [GitHub Actions]:

- `AWS_DEFAULT_REGION`: The AWS region Serverless will deploy to.
- `AWS_ACCESS_KEY_ID`: AWS access key ID.
- `AWS_SECRET_ACCESS_KEY`: AWS secret access key.
- `GH_TOKEN`: A personal access token that can trigger workflows.

These must be set manually.

### Secrets for Optional GitHub Actions

The version and format GitHub actions
require a user with write access to the repository,
including access to trigger workflows.
Set these additional secrets to enable the action:

- `GH_USER`: The GitHub user's username.
- `GH_TOKEN`: A personal access token for the user.
- `GIT_USER_NAME`: The GitHub user's real name.
- `GIT_USER_EMAIL`: The GitHub user's email.
- `GPG_PRIVATE_KEY`: The GitHub user's [GPG private key].
- `GPG_PASSPHRASE`: The GitHub user's GPG passphrase.

[GitHub Actions]: https://github.com/features/actions
[GPG private key]: https://github.com/marketplace/actions/import-gpg#prerequisites

## Contributing

Please submit and comment on bug reports and feature requests.

To submit a patch:

1. Fork it (https://github.com/makenew/serverless-benthos/fork).
2. Create your feature branch (`git checkout -b my-new-feature`).
3. Make changes.
4. Commit your changes (`git commit -am 'Add some feature'`).
5. Push to the branch (`git push origin my-new-feature`).
6. Create a new Pull Request.

## License

This Serverless project is licensed under the MIT license.

## Warranty

This software is provided by the copyright holders and contributors "as is" and
any express or implied warranties, including, but not limited to, the implied
warranties of merchantability and fitness for a particular purpose are
disclaimed. In no event shall the copyright holder or contributors be liable for
any direct, indirect, incidental, special, exemplary, or consequential damages
(including, but not limited to, procurement of substitute goods or services;
loss of use, data, or profits; or business interruption) however caused and on
any theory of liability, whether in contract, strict liability, or tort
(including negligence or otherwise) arising in any way out of the use of this
software, even if advised of the possibility of such damage.
