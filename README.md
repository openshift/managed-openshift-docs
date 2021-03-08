**This repo is no longer being updated. All existing content is being migrated back to the Core OpenShift docs repo. Do not submit a new PR to this repo. This repo will be shut down in the near future.**

This is the development and production branch for the revamped OpenShift Managed services docs.

Content merged here will appear in stage preview mode. If it passes acks, you can publish it live via Pantheon.

An attempt has been made to make this branch and workflow compatible with Pantheon V2. However, as that product is under active development, we are not splitting hairs trying to conform to all its guidelines currently. This branch and workflow will work for Pantheon V1 completely.

This is very much a WIP. Things will change and break. Go ahead and break them so we can get it right eventually before GA.

## Get started
To get started, fork this repo into your own GitHub space, and then clone on your local machine:

```
git clone git@github.com:<<your-github-username>>/managed-openshift-docs.git
cd managed-openshift-docs
git checkout 4.5
```

## Add new title
A `template` folder is provided in the `titles` folder to help with creating new titles.

To add a new title make a copy of the `template` folder (within the `titles` folder) and rename it based on your new title.

*For example*, to create a new title called `Release notes` copy the `template` folder within the `titles` folder and call it `release_notes`.

**Make sure to preserve the symbolic links or add these links yourself. There are three symbolic links in this `template` folder. On a Mac, for example, use `cp -a template release_notes`. The use of `-a` preserves the symbolic links.**

Then add and edit the files in this new `release_notes` folder.

This template folder contains a basic `docinfo.xml` and a `master.adoc`. You will need to edit both: `docinfo.xml` to add title information and `master.adoc` to add your assemblies.

### Next

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

## Set your upstream
Set up your upstream repo (we call it github here)

```
git remote add github https://github.com/openshift/managed-openshift-docs
```

## Rebase against upstream
In case others have made changes, you should rebase before pushing your content in:

```
git fetch github 4.5
git rebase github/4.5
```
## Workflow

* Add/edit titles and content.
* Push them to the repo.
* Get SME/QE/Peer reviews in your pull request. See section on QE/Peer reviews.
* If adding a new title, add them via Pantheon. See the example Pantheon `Template` book.
* Check your titles in Pantheon for build failures. Make changes if required.
* Make live via Pantheon when time is right.

## QE/Peer review

### Peer review
Team should follow the [peer review process](https://docs.google.com/document/d/1WN7k72PKxcPA__erp5TK-CefmS_sVwE3r40PvpmNk3E/edit) checklist as per OpenShift docs.
Each team member should get at least one other writing team member to review and ack the PR via a /lgtm in the PR before merging.

### QE review
* If the feature is shared with OCP, tag the OCP QE associate. See the list [here](https://bugzilla.redhat.com/describecomponents.cgi?product=OpenShift%20Container%20Platform).
* If the feature is OSD specific, tag Yufen Chang in the PR and/or corresponding Jira ticket.
* If the feature is ROSA specific, tag Jeremy Eder  and Yufen Chang in the PR and/or corresponding Jira ticket.
* If the feature is ARO specific, tag Mike Fiedler and Mike Gahagan in the PR and/or corresponding Jira ticket.

This QE review process has been discussed with the QE team and acked by them. Docs should not be merged without QE ack, except for typos.

## Guidelines

Follow the [OpenShift docs guidelines](https://github.com/openshift/openshift-docs/blob/master/contributing_to_docs/doc_guidelines.adoc) for docs creation with these exceptions:

* Add the `:system-module-type:` attribute at the top of your module (not assemblies). This will be one of `PROCEDURE`, `CONCEPT` or `REFERENCE`. This will change to `_module-type` in the future.
* Add `rosa_` as the prefix for any titles that are ROSA distribution specific. Add `rosa-` as the prefix for any assemblies and modules that are ROSA distribution specific. This will help us reuse content from core OSD while also creating distribution specific content.
