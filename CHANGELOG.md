# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) 
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]
*Note: unreleased changes are added here.*
<!-- Change types:
  ### Added, ### Changed, ### Fixed, ### Removed, ### Deprecated
-->

## 1.4.1 - 2017-03-17
### Fixed
* Pass network `opts` through to discovery-swarm.

## 1.4.0 - 2017-03-08
### Added
* `.datignore` support for ignoring files
* Callback on `joinNetwork` after first round of discovery
* Initial `pause` and `resume` API aliased to `join` and `leave`
* `stats.peers` API with new peer counts

### Fixed
* Better leave network, also closes swarm.
* Clone options passed to initArchive
* Set `opts.file` for archive owner without length
* `createIfMissing` passed to level options
* `dat.close()` twice sync errors
* Fix import without options
* (hyperdrive fix) sparse content archives

### Changed
* Remove automatic finalize for snapshot imports

## 1.3.8 - 2017-02-20
### Fixed
* Close archive after bad key on init.

## 1.3.7 - 2017-02-15
## Changed
* Rollback temporary changes from 1.3.6
* Set length on file option
* Remove hyperdrive version pin

## 1.3.6 - 2017-02-13
## Changed
* Temporary changes for critical replication bugs
* Pin hyperdrive to `7.13.2`
* Remove length option in `raf`
* Do not allow owner to download
* Do not set file option for owner

## 1.3.5 - 2017-02-04
## Fixed
* Key regression on resume

## 1.3.4 - 2017-02-03
## Fixed
* Call back with error if `opts.key` mismatches keys in database
* Fix options casting and improve errors
* Improve key handling for archive databases + debug info

## 1.3.3 - 2017-02-01
## Fixed
* Call back with error object on init archive

## 1.3.2 - 2017-02-01
## Fixed
* Do not mutate input args
* Call unreplicate on close to make sure data replication stops
* Throw error if close is called more than once

## 1.3.1 - 2017-01-25
## Fixed
* Real error message for `createIfMissing`

## 1.3.0 - 2017-01-25
## Added
* `createIfMissing` and `errorIfExists` options

## Deprecated
* `resume` option

## 1.2.4 - 2017-01-24
## Fixed
* fix regression in resuming archives without content by opening them first.

## 1.2.3 - 2017-01-24
## Fixed
* Learning things about `npm` versions!

## 1.2.2 - 2017-01-23
### Fixed
* Dowloaded file could have old bytes that weren't removed with updates. Issue #79.

## 1.2.1 - 2017-01-23
### Fixed
* Bug where opening archive on bad key returned without callback. Added timeout on open archive to make sure other key is tried before exiting.

## 1.2.0 - 2017-01-23
### Changed
* Read existing keys directly from hyperdrive instead of using the db. Allows for better resuming in any application.
* Count files much faster on import
* Add `opts.indexing` and default to true for when `source` = `dest`.

### Added
* Support for `drive` as first argument and [multidrive](https://github.com/yoshuawuyts/multidrive/) support
* `dat.leaveNetwork` - leave the network for this archive key.
* Added `dir` option to importer.
* Made it easier to require Dat as a module, without creating archive.

### Fixed
* Close archive after other things are closed
* Use discoveryKey for stats database (security)

### Deprecated
* Expose discovery swarm instance on `dat.network` instead of `dat.network.swarm`.

## 1.1.1 - 2017-01-06
### Fixed
* Resolve the path and untildify before creating archive

## 1.1.0 - 2017-01-03
### Added
* Use `opts.indexing` for importing.

## 1.0.0 - 2016-12-21
* dat-node released with a new API. [Read about changes](https://github.com/datproject/dat-node#moving-from-dat-js) from the old API.

## 0.1.1 - 2016-11-29
### Fixed
* Populate `dat.key` after archive opened ([#43](https://github.com/datproject/dat-node/pull/43))

### Changed
* Use hyperdiscovery instead of hyperdrive-archive-swarm ([#45](https://github.com/datproject/dat-node/pull/45))

## 0.1.0 - 2016-11-17
Released `dat-js` 4.0 as `dat-node` 0.1.

## Moved to dat-node.
*dat-node 0.1.0 === dat-js 4.0.0*

## 4.0.0 - 2016-11-16
*This will be the last major version of dat-js. This library will be moving to dat-fs, with a similar API.*

### Removed
* webrtc support (`opts.webrtc`, `opts.signalhub`)
* `opts.upload` changed to `opts.discovery.upload` (deprecated in 3.4.0)

### Fixed
* Error message for trying to download a dat to folder with existing dat.


## 3.8.2 - 2016-11-15
### Fixed
* Check type of keys on db resume

## 3.8.1 - 2016-11-15
### Fixed
* Progress incorrectly showing 100% with 0 bytes

## 3.8.0 - 2016-11-07
### Added
* Expose `dat.owner`, `dat.key`, `dat.peers`
* Support buffer keys
* Forward `db.open` errors

### Fixed
* Guard `archive.close` on `dat.close`

## 3.7.1 - 2016-10-29
### Fixed
* Create entryDone function once for downloads

## 3.7.0 - 2016-10-29
### Fixed
* Download file count for duplicate files

### Removed
* `stats.bytesProgress` on downloads

### Changed
* Upgrade to hyperdrive 7.5.0
* Use archive.blocks for stats on download with new hyperdrive functions.

## 3.6.0 - 2016-09-27
### Added
* `signalhub` option.

## 3.5.0 - 2016-09-22
### Added
* `opts.ignoreHidden` ignores hidden directories by default.

## 3.4.0 - 2016-09-14
### Changed
* Accept object for discovery: `{upload: true, download: true}`.

### Deprecated
* `upload` option (moved to `discovery.upload`). Will be removed in 4.0.0.

## 3.3.1 - 2016-09-06
### Fixed
* Emit `files-counted` event on Dat instance
* Include `stats` object on `file-counted` event

## 3.3.0 - 2016-09-06
### Added
* Add `webrtc` option

## 3.2.0 - 2016-09-01
### Added
* Upload option. `upload=false` will not upload data (allows download only option)

## 3.1.0 - 2016-09-01
### Added
* User `opts.ignore` extends default opts.

### Fixed
* Default ignore does not ignore files with .dat in them.

## 3.0.2 - 2016-08-26
### Fixed
* Default ignore config to ignore only `.dat` folder and files inside.

## 3.0.1 - 2016-08-18
### Fixed
* Fix hyperdrive-import-files bug on sharing directories

## 3.0.0 - 2016-08-18
### Added
* `dat.open()` function to initialize the `.dat` folder

### Removed
* `dat.on('ready')` event for initialization


## 2.x.x and earlier

* Port `lib/dat.js` file from the [Dat CLI](https://github.com/datproject/dat) library.

### Changed
* Use hyperdrive-import-files to import files on share
