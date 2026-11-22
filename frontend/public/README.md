# Public Folder — Frontend

## 1. Folder Overview

The `public/` folder contains static files that need to be served directly by the frontend application.

These files are made available by Vite without being imported into JavaScript or processed as part of the application module graph.

The folder is intended for static assets that need to retain their original filenames and paths.

## 2. What This Folder Should Contain

The `public/` folder may contain:

| File / Folder | Purpose |
|---|---|
| `favicon.ico` | Browser tab icon for EduMesh |
| `robots.txt` | Instructions for search engine crawlers, if required |
| `manifest.webmanifest` | Web application metadata, if required |
| `images/` | Static images that need to be referenced by direct URL |
| Other static files | Files that must be served directly without importing them |

Only assets that genuinely need direct public access should be placed here.

## 3. Public Folder vs Assets Folder

The `public/` folder and `src/assets/` folder serve different purposes.

| Public Folder | Assets Folder |
|---|---|
| Contains static files served directly | Contains assets imported into React or JavaScript |
| Files are referenced using their public URL paths | Files are imported into source files |
| Files are not processed through the normal module import pipeline | Assets can be processed by Vite during the build |
| Suitable for favicon and fixed public files | Suitable for component images, icons and illustrations |

### Example: Public File

A file stored at:

`public/images/edumesh-logo.png`

Can be referenced using:

```jsx
<img src="/images/edumesh-logo.png" alt="EduMesh Logo" />
```

### Example: Imported Asset

A file stored at:

`src/assets/images/edumesh-logo.png`

Can be imported using:

```jsx
import logo from "../assets/images/edumesh-logo.png";

<img src={logo} alt="EduMesh Logo" />
```

Choose the appropriate location depending on how the asset will be used.

## 4. Development Guidelines

1. Keep only static files that need direct public access in this folder.
2. Do not place React components or JavaScript application logic here.
3. Do not place CSS files for individual React components here.
4. Use `src/assets/` for assets that should be imported into application code.
5. Use meaningful and descriptive filenames.
6. Avoid duplicate copies of the same asset.
7. Do not store uploaded student resources or user-generated files in this folder.
8. Do not store environment variables, API keys, passwords or other secrets here.

## 5. Important Note

This folder is part of the planned EduMesh frontend structure.

Actual static files will be added when required during frontend development.

The presence of this README does not mean that all listed assets have already been created.
