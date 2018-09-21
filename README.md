# Metadata Editor – Automatic Updates

Automatic update system will check for the latest releases and update the application. For Metadata Editor we have set up an auto-updater using GitHub as a host.

## Set up the repository

Electron builder needs a GitHub access token to publish the application. Reference link to create the access token https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/.

Update the repository in the package.json file `"repository": "https://github.com/UserName/RepoName" `.

## Required builder configuration settings(electron-builder.yml)

appId: metadataeditor
publish:
    provider: github    
    token: <access-tocken>    
win:
    target: nsis-web    
nsisWeb:
    differentialPackage: true
    
    
target can be either nsis(installer) or nsis-web(web installer). web installer is a small setup which downloads the remaining components after it is run. 

## Publish 

Electron builder will package and publish the application. Add the script `ship": "build --win -p always" ` to build and publish the application

### GitHub release workflow

Go to the GitHub page and click releases. Draft a new release – Set the “Tag version” to the application version and prefixed it with “v”. eg: v1.0.0

Once the application is ready to publish, edit the version field in the package.json and run the following command.
`npm run ship`

Go to the GitHub page and select the draft release and click ‘edit’ and then ‘publish release’

![GitHubReleases](github_releases.png?raw=true "GitHubReleases")
