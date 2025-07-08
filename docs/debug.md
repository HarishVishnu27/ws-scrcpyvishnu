### Client

1. Build dev version (will include source maps):
> npm run dist:dev

2. Run from `dist` directory:
> npm run start

3. Use the browser's built-in developer tools or your favorite IDE.

### Node.js server

1. `npm run dist:dev`
2. `cd dist`
3. `node --inspect-brk ./index.js`

__HINT__: you might want to set `DEBUG` environment variable (see [debug](https://github.com/visionmedia/debug)):
> DEBUG=* node  --inspect-brk ./index.js

### iOS Device Debugging

For iOS devices, debugging is primarily done through:

1. **WebDriverAgent logs** - Check XCode console and device logs
2. **Browser DevTools** - Use Safari Developer tools for web client debugging
3. **ws-qvh logs** - If using ws-qvh for streaming, check terminal output
4. **Server logs** - Monitor Node.js server output with DEBUG environment variable
