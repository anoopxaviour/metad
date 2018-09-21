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
