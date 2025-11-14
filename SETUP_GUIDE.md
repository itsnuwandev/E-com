# Digitic E-Commerce Project - Setup Guide

This is a full-stack MERN (MongoDB, Express, React, Node.js) e-commerce application with three main components:

## Project Structure

- **digitic-backend-master/** - Node.js/Express backend API
- **digitic-admin-master/** - React admin panel
- **Digitic-E-Commerce-Frontend-main/** - React customer-facing storefront

---

## Setup Instructions

### 1. Backend Setup (digitic-backend-master)

```bash
cd digitic-backend-master
npm install
```

#### Configure Environment Variables

Edit `.env` file and update with your credentials:

```env
PORT=5000
MONGODB_URL=mongodb://localhost:27017/digitic

JWT_SECRET=your-secure-jwt-secret-key
JWT_EXPIRE=3d

# Email Configuration (Gmail recommended)
MAIL_ID=your-email@gmail.com
MP=your-gmail-app-password

# Cloudinary (for image uploads)
CLOUD_NAME=your-cloudinary-name
API_KEY=your-cloudinary-key
API_SECRET=your-cloudinary-secret
```

**Important Notes:**

- For Gmail, use an [App Password](https://support.google.com/accounts/answer/185833) instead of your regular password
- Create a free [Cloudinary account](https://cloudinary.com/) for image uploads
- Make sure MongoDB is running on your system

#### Start Backend Server

```bash
npm start
# or for development with auto-reload
npm run server
```

Backend will run on: http://localhost:5000

---

### 2. Admin Panel Setup (digitic-admin-master)

```bash
cd digitic-admin-master
npm install
```

#### Configure Environment Variables

The `.env` file is already created. Update if needed:

```env
REACT_APP_API_URL=http://localhost:5000/api/
```

#### Start Admin Panel

```bash
npm start
```

Admin panel will run on: http://localhost:3000

**Default Admin Login:**

- You'll need to create an admin user through the backend API first
- Use the `/api/user/admin-login` endpoint

---

### 3. Customer Frontend Setup (Digitic-E-Commerce-Frontend-main)

```bash
cd Digitic-E-Commerce-Frontend-main
npm install
```

#### Configure Environment Variables

The `.env` file is already created. Update if needed:

```env
REACT_APP_API_URL=http://localhost:5000/api/
```

#### Start Customer Frontend

```bash
npm start
```

Frontend will run on: http://localhost:3001 (or next available port)

---

## Running All Applications

You need to run all three applications simultaneously:

### Terminal 1 - Backend

```bash
cd digitic-backend-master
npm run server
```

### Terminal 2 - Admin Panel

```bash
cd digitic-admin-master
npm start
```

### Terminal 3 - Customer Frontend

```bash
cd Digitic-E-Commerce-Frontend-main
npm start
```

---

## Features

### Customer Frontend

- Product browsing and search
- Shopping cart
- Wishlist
- User authentication
- Order placement
- Blog section
- Product reviews and ratings

### Admin Panel

- Product management (CRUD)
- Order management
- Customer management
- Blog management
- Category management
- Brand management
- Color management
- Coupon management
- Enquiry management
- Image uploads

### Backend API

- RESTful API
- JWT authentication
- MongoDB database
- Image upload with Cloudinary
- Email notifications
- Order processing
- User management

---

## Database Setup

Make sure MongoDB is installed and running:

```bash
# Start MongoDB (if not running as service)
mongod
```

The application will automatically create the `digitic` database on first run.

---

## Troubleshooting

### Port Already in Use

If port 3000 is already in use, React will prompt to use another port. Accept it.

### MongoDB Connection Error

- Ensure MongoDB is running
- Check the `MONGODB_URL` in `.env`
- Default: `mongodb://localhost:27017/digitic`

### CORS Issues

The backend has CORS enabled. If you change ports, you may need to update CORS settings in `index.js`

### Image Upload Issues

- Verify Cloudinary credentials in `.env`
- Check your Cloudinary dashboard for upload limits

---

## API Endpoints

Base URL: `http://localhost:5000/api/`

### User Routes

- POST `/user/register` - Register new user
- POST `/user/login` - User login
- POST `/user/admin-login` - Admin login
- GET `/user/wishlist` - Get user wishlist
- POST `/user/cart` - Add to cart

### Product Routes

- GET `/product` - Get all products
- GET `/product/:id` - Get single product
- POST `/product` - Create product (admin)
- PUT `/product/:id` - Update product (admin)
- DELETE `/product/:id` - Delete product (admin)

### Blog Routes

- GET `/blog` - Get all blogs
- GET `/blog/:id` - Get single blog
- POST `/blog` - Create blog (admin)

[... and many more routes]

---

## Technologies Used

### Frontend

- React 18
- Redux Toolkit
- React Router v6
- Axios
- React Toastify
- Formik & Yup (validation)
- Ant Design (admin panel)

### Backend

- Node.js
- Express
- MongoDB & Mongoose
- JWT
- Bcrypt
- Cloudinary
- Nodemailer
- Multer & Sharp (image processing)

---

## Security Notes

1. **Never commit `.env` files** to version control
2. Change default JWT secret to a strong random string
3. Use environment-specific `.env` files for production
4. Enable HTTPS in production
5. Implement rate limiting for API endpoints
6. Validate and sanitize all user inputs

---

## Production Deployment

Before deploying to production:

1. Update `.env` files with production values
2. Update `REACT_APP_API_URL` to your production API URL
3. Build frontend apps:
   ```bash
   npm run build
   ```
4. Set up proper MongoDB hosting (MongoDB Atlas recommended)
5. Configure environment variables on your hosting platform
6. Enable HTTPS
7. Set up proper backup procedures

---

## Need Help?

- Check the console for error messages
- Verify all environment variables are set correctly
- Ensure all dependencies are installed
- Make sure all three applications are running
- Check MongoDB connection

---

## Created Files

This setup included the following new files:

**Backend:**

- `.env` - Environment configuration
- `.env.example` - Environment template

**Admin Panel:**

- `.env` - Frontend API configuration
- `.env.example` - Config template

**Customer Frontend:**

- `.env` - Frontend API configuration
- `.env.example` - Config template
- `src/app/store.js` - Redux store configuration
- `src/utils/axiosConfig.js` - Axios configuration
- `src/utils/base_url.js` - API base URL
- `src/features/user/userSlice.js` - User state management
- `src/features/user/userService.js` - User API service
- `src/features/products/productSlice.js` - Product state management
- `src/features/products/productService.js` - Product API service
- `src/features/blogs/blogSlice.js` - Blog state management
- `src/features/blogs/blogService.js` - Blog API service
- `src/features/contact/contactSlice.js` - Contact state management
- `src/features/contact/contactService.js` - Contact API service

---

Happy coding! 🚀
