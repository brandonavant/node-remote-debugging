# node-remote-debugging

Simple instructions for remotely debugging a node.js applications. Please follow the steps below:

## Starting Debugging Session on Remote Server

1. Connect to your remote server via SSH.
2. Once connected, navigate to your node application's directory (e.g. ```~/apps/demo/```).
3. Run the following command replacing the placeholder with the name of your application (I used ```app.js```): ```node --inspect-brk app.js```
4. You will receive a message indicating that the debugger has been attached.

## Connecting Chrome DevTools to Remote Debug Session

1. Open a tab in chrome and navitate to ```chrome://inspect```.
2. You should see an option for *Open dedicated DevTools for Node*; if you do, click it; if you don't, update Chrome.
3. On the screen that appears, you should see a couple of entries: ```localhost:9222``` and ```localhost:9229```.
4. To link your client machine to the remote debugging session, you will need to create a tunnel in a separate terminal using the command ```ssh -N -L 9222:localhost:9229 -i [PATH_TO_PEM_FILE].pem user@[REMOTE_HOST:PORT]```.
5. At this point your DevTools should hit the first line of your code; et voilà, you're ready to debug!
