# Blog App

A modern blogging platform frontend built with **React** and powered by **Appwrite** as the backend-as-a-service (auth, database, and file storage). Users can sign up, log in, write rich-text posts with a built-in editor, upload featured images, and manage their own posts.

## Features

- **Authentication**
  - Sign up / log in / log out using Appwrite's auth service
  - Persistent auth state managed with Redux Toolkit
  - Protected routes via an `AuthLayout` wrapper
- **Posts**
  - Create, edit, and delete blog posts
  - Rich text editing with TinyMCE (`@tinymce/tinymce-react`)
  - Upload and manage featured images via Appwrite Storage
  - Toggle post status (active/inactive) to control visibility
  - View all posts or a single post by slug
- **UI**
  - Responsive layout with Header, Footer, and reusable components (Button, Input, Select, Logo, Postcard)
  - Styled with Tailwind CSS

## Tech Stack

| Layer            | Technology                              |
|--------------------|--------------------------------------------|
| Library             | React 19                                     |
| Backend-as-a-Service| Appwrite (Auth, Databases, Storage)         |
| State Management    | Redux Toolkit, React Redux                   |
| Routing             | React Router DOM v7                          |
| Forms               | React Hook Form                              |
| Rich Text Editor    | TinyMCE                                      |
| HTML Rendering      | html-react-parser                            |
| Styling             | Tailwind CSS v4                              |
| Build Tool           | Vite                                         |

## Project Structure

```
src/
├── main.jsx                  # App entry point
├── App.jsx                   # Root component with routing
├── appwrite/
│   ├── appwriteConfig.js       # Service class: createPost, updatePost, deletePost,
│   │                            # getPost, getActivePosts, uploadFile, deleteFile
│   └── auth.js                 # AuthService class: createAccount, login,
│                                # getCurrentUser, logOut
├── config/
│   └── config.js               # Reads Appwrite env variables
├── store/
│   ├── store.js                # Redux store setup
│   └── authSlice.js            # Auth state slice
├── components/
│   ├── Header/                 # Header.jsx, LogoutBtn.jsx
│   ├── container/Container.jsx
│   ├── postForm/PostForm.jsx   # Create/edit post form
│   ├── AuthLayout.jsx          # Route protection wrapper
│   ├── Login.jsx / Signup.jsx
│   ├── Postcard.jsx            # Post preview card
│   ├── RTE.jsx                 # Rich text editor wrapper
│   ├── Button.jsx / Input.jsx / Select.jsx / Logo.jsx / Footer.jsx
│   └── index.js                # Component exports
└── pages/
    ├── Home.jsx
    ├── AllPost.jsx
    ├── AddPost.jsx
    ├── EditPost.jsx
    ├── Post.jsx
    ├── Login.jsx
    └── Signup.jsx
```

## Getting Started

### Prerequisites

- Node.js (v18+ recommended)
- An [Appwrite](https://appwrite.io/) project with:
  - A Database and a Collection set up for posts (fields: `title`, `content`, `featuredImg`, `status`, `userId`)
  - A Storage Bucket set up for featured images

### Installation

1. Clone the repository
   ```bash
   git clone https://github.com/Roshan1401/Blog-App.git
   cd Blog-App
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Create a `.env` file in the project root with your Appwrite project details:
   ```env
   VITE_APPWRITE_URL=https://cloud.appwrite.io/v1
   VITE_APPWRITE_PROJECT_ID=your_appwrite_project_id
   VITE_APPWRITE_DATABASE_ID=your_appwrite_database_id
   VITE_APPWRITE_COLLECTION_ID=your_appwrite_collection_id
   VITE_APPWRITE_BUCKET_ID=your_appwrite_bucket_id
   ```

4. Start the development server
   ```bash
   npm run dev
   ```

   The app will be available at `http://localhost:5173`.

## Scripts

| Command           | Description                                |
|---------------------|------------------------------------------------|
| `npm run dev`        | Starts the Vite development server               |
| `npm run build`      | Builds the app for production                     |
| `npm run preview`    | Previews the production build locally             |
| `npm run lint`       | Runs ESLint on the codebase                        |

## License

ISC
