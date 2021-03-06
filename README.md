# Makefile.Includes

This a set of Makefile files with many customized targets.

## Installation

Recommended solution to use it is to register it as a submodule into your repository with command similar to:

	git submodule add git@github.com:a4099181/Makefile.Includes.git

Then create your Makefile file and place includes you want into it. Just like that:

	# Your Makefile file
	include Makefile.Includes/Makefile.basic
	include Makefile.Includes/Makefile.nuget

## Content

#### targets available in *Makefile.basic*
  * `clean` - it completely cleans up your working tree with hard-core command `git clean -dxf`.

#### targets available in *Makefile.haskell*
  * `hindent` - applies [hindent] utility to all `.hs` files.
  * `scan` - applies [scan] utility to all `.hs` files.
  * `test` - it executes Hspec tests and is just shortcut for `runhaskell -isrc -itest test/Spec.hs`.

#### targets available in *Makefile.nuget*
  * `nuget-pack` - it looks for *.nuspec* files, builds related *.csproj* file with *release* configuration and packs the output into NuGet package. Please note, that *.nuspec* file and *.csproj* should have the same basename.
  * `nuget-push` - it looks for *.nupkg* files and pushes them to source provided by `${nuget-source}` variable.
  * `nuget-setApiKey` - it sets API key for source provided by `${nuget-source}` variable. Please note, that you should pass API key into `${nuget-apikey}` variable.

    ```shell
    make nuget-setApiKey nuget-apikey=<your-api-key-here>
    ```

#### targets available in *Makefile.vagrant*
  * `box-hyperv` - creates `tar` archive for current folder. That is the way that hyper-v virtual machine becomes vagrant box.

#### targets available in *Makefile.vsix*
  * `download` - resolves current download link and downloads it.
  * `install` - installs downloaded Visual Studio extensions.
  * `clean` - removes download destination folder.

  Complete solution to install Visual Studio Extension:

  ```shell
  make download install clean vsix-id=<vs-extension-guid>
  ```

[hindent]: https://github.com/chrisdone/hindent
[scan]: http://hackage.haskell.org/package/scan
