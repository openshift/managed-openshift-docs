This is the development and production branch for the revamped OpenShift Dedicated docs.

Content merged here will appear in stage preview mode. If it passes acks, you can publish it live via Pantheon.

An attempt has been made to make this branch and workflow compatible with Pantheon V2. However, as that product is under active development, we are not splitting hairs trying to conform to all its guidelines currently. This branch and workflow will work for Pantheon V1 completely.

## Get started
To get started, clone this repo on your local machine (no need to fork into your own GitLab instance):

```
git clone git@gitlab.cee.redhat.com:red-hat-openshift-dedicated-documentation/doc-4.git
git checkout 4.5
```

## Add new title
A `template` folder is provided in the root level to help with creating new titles.

To add a new title copy the folder `template` into the `titles` folder and rename it based on your new title.

For example, to create a new title called `Release notes` copy the `template` folder into the `titles` folder and call it `release_notes`.

**Make sure to preserve the symbolic links. There are three symbolic links in this `template` folder. On a Mac, for example, use `cp -a template release_notes`. The use of `-a` prserves the symbolic links.**

Then add and edit the files in this new `release_notes` folder.

This template folder contains a basic `docinfo.xml` and a `master.adoc`. You will need to edit both: `docinfo.xml` to add title information and `master.adoc` to add your assemblies.

* Add your assemblies in the top-level `assemblies` folder.
* Add your modules in the top-level `modules` folder.
* Add your images in the top-level `_images` folder.

## Add/edit content
Make changes in your local machine, and once done, add content back into the repo. You may want to rebase against origin regularly to avoid conflicts on pushing (see next section):

```
git add <files>
git commit -m "<Add change description>"
git push origin 4.5
```

## Rebase against origin
In case others have made changes, you should rebase before pushing your content in:

```
git fetch origin 4.5
git rebase origin/4.5
```
## Workflow

* Add/edit titles and content.
* Push them to the repo.
* Check your titles in Pantheon for build failures. Make changes if required.
* Get QE/Peer review acks in Pantheon stage builds.
* Make live via Pantheon.
