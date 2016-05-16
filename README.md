## FastBoot GitLab Downloader

[![Latest NPM release][npm-badge]][npm-badge-url]
[![Dependency Status][dependency-badge]][dependency-badge-url]
[![TravisCI Build Status][travis-badge]][travis-badge-url]
[![Code Climate][codeclimate-badge]][codeclimate-badge-url]

[npm-badge]: https://img.shields.io/npm/v/fastboot-gitlab-downloader.svg
[npm-badge-url]: https://www.npmjs.com/package/fastboot-gitlab-downloader
[dependency-badge]: https://img.shields.io/david/buschtoens/fastboot-gitlab-downloader.svg
[dependency-badge-url]: https://david-dm.org/buschtoens/fastboot-gitlab-downloader
[travis-badge]: https://img.shields.io/travis/buschtoens/fastboot-gitlab-downloader/master.svg?label=TravisCI
[travis-badge-url]: https://travis-ci.org/buschtoens/fastboot-gitlab-downloader
[codeclimate-badge]: https://img.shields.io/codeclimate/github/buschtoens/fastboot-gitlab-downloader.svg
[codeclimate-badge-url]: https://codeclimate.com/github/buschtoens/fastboot-gitlab-downloader

This downloader for the [FastBoot App Server][app-server] works with GitLab
Builds to download and unzip the latest build artifacts of your deployed
application.

[app-server]: https://github.com/ember-fastboot/fastboot-app-server

To use the downloader, configure it with your GitLab API token and your repo:

```js
const FastBootAppServer = require('fastboot-app-server');
const GitLabDownloader  = require('fastboot-gitlab-downloader');

let notifier = new GitLabDownloader({
  url:   'http://gitlab.example.com',
  token: '0123456789abcdefghij'

  project: 'buschtoens/fastboot-test-app', // or numeric project id
  ref:     'master'                        // optional, defaults to 'master'

  path: 'dist' // optional path of the `dist` directory, defaults to 'dist'
});

let server = new FastBootAppServer({
  downloader: downloader
});
```

When the downloader runs, it will download the zip archive for the most recent
successful build for the specified project and ref.

If you like this, you may also be interested in the companion
[fastboot-gitlab-notifier](https://github.com/buschtoens/fastboot-gitlab-notifier).

You might also like [fastboot-gitlab-app-server](https://github.com/buschtoens/fastboot-gitlab-app-server),
a pre-made and optionally dockerized FastBoot App Server that uses the GitLab
notifier and downloader.
