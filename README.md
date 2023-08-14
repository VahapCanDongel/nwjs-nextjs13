NW.js and Next JS 13 - Using Next JS 13 to build desktop applications

To run:

```bash
npm run dev
# then
npm run nw
```

Bundling your NW.js application involves packaging your Next.js app and NW.js runtime into a distributable format for different platforms (Windows, macOS, Linux). Here's a step-by-step guide to bundle everything:

### 1. Build the Next.js App:

Before bundling, ensure you've built your Next.js app for production:

```bash
npm run build
```

### 2. Set Up NW.js Builder:

[NW.js Builder](https://github.com/nwjs-community/nw-builder) is a tool that lets you compile and package NW.js apps.

Install it as a dev dependency:

```bash
npm install nw-builder --save-dev
```

### 3. Add a Build Script:

In your `package.json`, add a script to build the desktop app:

```json
"scripts": {
  ...
  "build-desktop": "nwbuild -p win64,osx64,linux64 ."
},
```

This script tells NW.js Builder to create builds for Windows (64-bit), macOS (64-bit), and Linux (64-bit). You can adjust the platforms and architectures as needed.

### 4. Bundle the Application:

Run the build script:

```bash
npm run build-desktop
```

This will create builds for the specified platforms in a `build` directory in your project root.

### 5. Distribute the Bundled Application:

Inside the `build` directory, you'll find folders for each platform you specified. Each folder contains the bundled application and the NW.js runtime. You can distribute these folders to users, and they can run the application without needing to install anything else.

**Note**: If your application has external dependencies or assets, ensure they are included in the build directory. You might need to adjust paths or configurations to ensure everything works correctly in the bundled version.

That's it! You now have a bundled desktop application built with Next.js and NW.js, ready for distribution.
