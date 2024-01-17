# forTestOnly
# ghcr-badges

[![docker]](https://github.com/kit-data-manager/forTestOnly/pkgs/container/fortestonly)
[![currentVersion]](https://github.com/kit-data-manager/forTestOnly/pkgs/container/fortestonly)
[![size]](https://github.com/kit-data-manager/forTestOnly/pkgs/container/fortestonly)


[docker]: <https://ghcr-badge.egpl.dev/kit-data-manager/fortestonly/tags?trim=major&color=steelblue&ignore=main,latest&label=docker versions>
[currentVersion]: <https://ghcr-badge.egpl.dev/kit-data-manager/fortestonly/latest_tag?trim=major&color=steelblue&label=current version>
[size]: <https://ghcr-badge.egpl.dev/kit-data-manager/fortestonly/size?color=steelblue&label=size>

For pulling latest image please use:
```
$> docker pull ghcr.io/kit-data-manager/fortestonly:latest
```
# Packaging branches
If there are old versions which should be further maintained it 
would be possible to pack them in a separate package.

**Example**

There are two versions available: 
- v2.3.4 and 
- v1.5.6
 
and both should be updated/maintained also in future.

Than you should do the following:
```
# Checkout v1.5.6 and create an extra branch for it:
> git checkout v1.5.6
# Create an extra branch
> git checkout -b Version_1
# package this version to a new package
> git tag Version_1-v1.5.6
# push this tag to gitHub 
> git push --tags
```
After a few minutes there should be a new package available called:
```
YOUR_REPO-version_1:version_1-v1.5.6 (always available via 'latest' tag)
```

:information_source:
The tag has to be in the form: '\*-v\*'

It's recommended to use [Semantic Versioning](https://semver.org/spec/v2.0.0.html) after the 'v' 
and a unique string at the beginning.

## Fixing an old version
```
# Checkout branch for the version you want to fix (e.g.: Version_1)
> git checkout Version_1
# Fix version and push it to github
> nano YOUR_FILE
> git add YOUR_FILE
> git commit -m "Fix ...."
> git push --set-upstream origin Version_1
# After that tag the new version in the same way as before
> git tag Version_1-v1.5.7
> git push --tags
```
After a few minutes there should be a version in the package available called:
```
YOUR_REPO-version_1:version_1-v1.5.7 (also available via 'latest' tag)
```
 
# FAQ
- Why should I use an extra package instead only tagging with the new version?
  - If users rely on a specific branch(e.g. Version_1) they always have to chek for new 
versions. Using an extra package they can use the latest tag instead and only 
force a pull every time they want to update without thinking about versions.
- I want to get rid of the prefix in the tag. Is this possible?
  - Yes it is. But therefore you have to create your own github action with adopted settings.
See .github/workflows/docker-publish.yml as starting point.
:warning: Tags have to be unique inside the repo, because they are not bound to a specific
branch.

# Links
For more information about publishing images to GitHub Packages see:
- https://docs.github.com/en/actions/publishing-packages/publishing-docker-images#publishing-images-to-github-packages
