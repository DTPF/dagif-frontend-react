# DaGif — Frontend

Social GIF-sharing platform where users can upload, browse, search and interact with GIFs. Built with React and TypeScript.

## Features

- User registration and authentication
- GIF upload from local device
- Browse and search GIFs by keywords and categories
- User profiles with upload history
- Like and comment on GIFs
- Share GIFs via direct links
- PWA with service workers (Workbox)
- Responsive design for mobile and desktop

## Tech Stack

- **Frontend:** React, TypeScript, Ant Design, Sass
- **Auth:** Auth0
- **Media storage:** Cloudinary
- **PWA:** Workbox service workers

## Getting Started

1. Clone and set up the backend first — see [dagif-backend-node](https://github.com/DTPF/dagif-backend-node)
2. Clone this repo: `git clone https://github.com/DTPF/dagif-frontend-react.git`
3. Install dependencies: `npm install`
4. Copy `.env.example` and configure Auth0 and Cloudinary credentials
5. Start the dev server: `npm run dev`

The app runs at `http://localhost:5170`

## Related

- [dagif-backend-node](https://github.com/DTPF/dagif-backend-node) — Express.js backend
