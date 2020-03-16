# ServiceNow Developer Configuration

### Github Integration

Use Github as your code repository for scoped custom application code. ServcieNow provides a sample repository called NeedIt, https://github.com/ServiceNow/devtraining-needit-orlando, for Developer Training. See the Developer site to understand how to setup Github integration fro the NeedIt repository. Be aware the initial repository is empty when the master branch is selected, switching to a different tag for specific exercises will link the relevant files.

Loading a tag and then setting up the VS Code extension will enable local development with the repository files.

### Extension for VS Code

Currently now-cli is not integrated into the Extension, this is work in progress.

The ServiceNow Extensions for VS Code includes tools for developing on the Now Platform. The extension adds several functions to your Visual Studio Code (VS Code) implementation, https://docs.servicenow.com/bundle/orlando-application-development/page/build/applications/reference/vscode-functions.html.

First install the Extensions, https://docs.servicenow.com/bundle/orlando-application-development/page/build/applications/task/vscode-installation.html.

Follow the guide to Setup a workspace, https://docs.servicenow.com/bundle/orlando-application-development/page/build/applications/task/setup-workspace.html.

Now create a new Project for the application you’re working on. In this sample the above NeedIt application is used.
[Image: image.png][Image: image.png][Image: image.png][Image: image.png]Needless to say it’s better to create a developer access role specifically for the scope you’re developing in.
[Image: image.png][Image: image.png][Image: image.png][Image: image.png][Image: image.png]After this a files will be loaded to the local system project folder.
[Image: image.png]The process will also execute an `npm install` visible in the Now Console window.
[Image: image.png]Now it’s possible to edit the script files locally and sync them with the ServiceNow instance, https://docs.servicenow.com/bundle/orlando-application-development/page/build/applications/task/sync-current-file.html.
[Image: image.png]
### now-cli

With Orlando the now-cli has been exposed and can be used to build components for the current ServiceNow UI Framework, Seismic. For more information refer to the Developer site, [https://developer.servicenow.com/dev.do#!/guide/orlando/now-experience/cli/getting-started/.](https://developer.servicenow.com/dev.do#!/guide/orlando/now-experience/cli/getting-started/) Be aware that the content is based on your access, if you login as an employee you get information about the internal setup.

Since the CLI uses the LTS version of Node you might want to install nvm for managing Node versions, https://github.com/nvm-sh/nvm#installing-and-updating.
Install NVM, `curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.3/install.sh | bash`
Install Node, `nvm install --lts`
Default Node version, `nvm alias default 12.16.1`
[Image: image.png]
If needed use yarn instead of npm to setup the cli, `yarn global add @servicenow/cli`.
[Image: image.png]
The cli should be available.
[Image: image.png]
Follow the guide in the docs to start developing Components for Workspace, https://docs.servicenow.com/bundle/orlando-servicenow-platform/page/build/components/concept/custom-components.html.

# Component Development

### Setup Project

Connect to your development instance
`now-cli login --host https://jws202003demo.service-now.com --method basic --username admin --password ‘xxxxxxxxxx’`
Create a folder for the project and cd into the project folder
`mkdir cmpCall`
`cd cmpCall`
[Image: image.png]
Project scaffolding
`now-cli project --name cmp-call --description 'Calling component'`
[Image: image.png]You can check Application Manager to verifiy the component and scope created.
[Image: image.png]
Install dependencies
`yarn install`
[Image: image.png]Once done the project is available in VS Code.
[Image: image.png]
Change the View.
[Image: image.png]Run your Component locally.
`now-cli develop`
[Image: image.png][Image: image.png]Feel free to add the component to a source control repository, `git init`.

These type of new components will only be available for Workspace through the UI Builder. Configure the now-ui.json for UI Builder support, https://developer.servicenow.com/dev.do#!/guide/orlando/now-experience/cli/ui-builder/ and https://docs.servicenow.com/bundle/orlando-servicenow-platform/page/build/components/task/view-in-uib.html.

[Image: image.png]Deploy to the instance with `now-cli deploy`.
[Image: image.png]Now add the Component to a Workspace, in this case a new Workspace. Navigate to Workspace Experience > Administration > All Workspaces. Make sure you have the right Scope.
[Image: image.png]
Pick New and fill out the Form.
[Image: image.png]Follow the wizard, feel free to select what’s needed. Click Done at the end.
[Image: image.png]Open the Workspace page from the list of Workspaces and click Open in UI Builder.
[Image: image.png]

Create a new landing page.
[Image: image.png]
[Image: image.png]Then switch to Add component and drag and drop the component to the Workspace.
[Image: image.png]
