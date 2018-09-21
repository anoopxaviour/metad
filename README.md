# Metadata Editor – Automatic Updates

Metadata Editor installer includes an automaic updater that can check for, download and install updates. Metadata Editor is packaged with electron builder and used electron-updater module which allows update from GitHub or any other static file host.

## Set up the repository

For Metadata Editor, we used GitHub as a host and electron builder needs a GitHub access token to publish the application. Reference link to create the access token https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/.

## Update repository in package.json
`"repository": "https://github.com/UserName/RepoName" `.

## Required builder configuration settings(electron-builder.yml)

```sh
appId: metadataeditor
publish:
    provider: github    
    token: <access-tocken>    
win:
    target: nsis-web    
nsisWeb:
    differentialPackage: true
```
    
target can be either nsis(installer) or nsis-web(web installer). web installer is a small setup which downloads the remaining components after it is run. Please see the link https://www.itechtics.com/offlinestandalone-installer-vs-webonline-installer-advantages-disadvantages/ for detailed explanation.

## Publish 

Electron builder will package and publish the application. Add the script `ship": "build --win -p always" ` to build and publish the application

### GitHub release workflow

Go to the GitHub page and click releases. 

![GitHubReleases](github_releases.png?raw=true "GitHubReleases")

* Draft a new release – Set the “Tag version” to the application version and prefixed it with “v”. eg: v1.0.0

* Once the application is ready to publish, edit the version field in the package.json and run the following command.
`npm run ship`

* Go to the GitHub page and select the draft release and click ‘edit’ and then ‘publish release’

