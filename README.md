# event-emitter

safe-event-emitter
An EventEmitter that isolates the emitter from errors in handlers. If an error is thrown in a handler it is caught and re-thrown inside of a setTimeout so as to not interrupt the emitter's code flow.

The API is the same as a core EventEmitter.

Install
$ yarn add '@metamask/safe-event-emitter'
Usage
import SafeEventEmitter from '@metamask/safe-event-emitter';

const ee = new SafeEventEmitter();
ee.on('boom', () => { throw new Error(); });
ee.emit('boom'); // No error here

// Error is thrown after setTimeout
Release & Publishing
The project follows the same release process as the other libraries in the MetaMask organization:

Create a release branch
For a typical release, this would be based on master
To update an older maintained major version, base the release branch on the major version branch (e.g. 1.x)
Update the changelog
Update version in package.json file (e.g. yarn version --minor --no-git-tag-version)
Create a pull request targeting the base branch (e.g. master or 1.x)
Code review and QA
Once approved, the PR is squashed & merged
The commit on the base branch is tagged
The tag can be published as needed
Running tests
yarn test
