# Assets Folder — Frontend

## 1. Folder Overview

The `assets/` folder contains images, icons, illustrations and other static assets used by the EduMesh frontend application.

These assets are imported into React components or JavaScript files when required.

This folder helps keep visual resources organized and separate from application logic.

## 2. Planned Folder Structure

```text
assets/
│
├── README.md
│
├── images/
├── icons/
└── illustrations/
```

The subfolders will be created when actual assets are added.

| Folder | Responsibility |
|---|---|
| `images/` | Imported images used throughout the application |
| `icons/` | Custom icon files used in the interface |
| `illustrations/` | Illustrations used in pages and interface sections |

Additional asset categories may be introduced when required.

## 3. What Belongs in This Folder?

Examples of assets that may be stored here include:

### Images

- EduMesh logo used inside application components.
- Subject-related images.
- Learning resource thumbnails.
- Profile placeholder images.
- Decorative interface images.

### Icons

- Custom navigation icons.
- Feature-specific icons.
- Interface symbols not supplied by the chosen icon library.

### Illustrations

- Login and registration illustrations.
- Empty-state illustrations.
- Dashboard illustrations.
- Educational illustrations.

Only assets actually needed by the application should be added.

## 4. Importing Assets

Assets stored inside `src/assets/` should be imported into the relevant React or JavaScript files.

Example:

```jsx
import logo from "../../assets/images/edumesh-logo.png";

function Logo() {
  return (
    <img src={logo} alt="EduMesh Logo" />
  );
}

export default Logo;
```

The relative import path should be adjusted according to the location of the component.

Vite processes imported assets as part of the application build.

## 5. Assets Folder vs Public Folder

| `src/assets/` | `public/` |
|---|---|
| Assets imported into source files | Static files served directly |
| Processed by Vite through imports | Not processed through the normal module import pipeline |
| Suitable for component images and illustrations | Suitable for favicon and files requiring direct public URLs |
| Referenced through imports | Referenced through public URL paths |

Choose the appropriate folder based on how the file will be accessed.

## 6. Development Guidelines

1. Keep imported visual assets inside `assets/`.
2. Organize assets into meaningful subfolders.
3. Use descriptive and consistent filenames.
4. Prefer optimized image formats and reasonable file sizes.
5. Avoid duplicate copies of the same asset.
6. Do not store React components or application logic here.
7. Do not store user-uploaded learning resources here.
8. Do not store passwords, API keys or other sensitive information here.
9. Use the `public/` folder when an asset needs to be served directly by its public URL.

## 7. Important Note

This folder is intended for static assets used by the EduMesh frontend.

Actual images, icons and illustrations will be added progressively during frontend development.

The presence of this README does not mean that all listed assets or subfolders have already been created.
