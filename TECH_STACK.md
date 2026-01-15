# Neurofy Technology Stack

## Frontend Technologies

### Core Framework
- **Next.js 14**: React framework with App Router
- **React 18**: UI library with hooks and concurrent features
- **TypeScript**: Type-safe JavaScript

### UI & Styling
- **Tailwind CSS**: Utility-first CSS framework
- **shadcn/ui**: High-quality React components
- **Radix UI**: Accessible component primitives
- **Framer Motion**: Animation library
- **Lucide React**: Icon library

### State Management
- **React Hooks**: useState, useEffect, useContext
- **Custom Hooks**: useSubscription, useAnalytics
- **Firebase Realtime Listeners**: Real-time data sync

### Forms & Validation
- **React Hook Form**: Form state management
- **Zod**: Schema validation

### Data Fetching
- **Fetch API**: Native browser API
- **Axios**: HTTP client (for some endpoints)
- **Firebase SDK**: Real-time database access

### Video & Media
- **React Player**: Video playback
- **FFmpeg.wasm**: Client-side video processing
- **RecordRTC**: Video recording

### Charts & Visualization
- **Chart.js**: Charting library
- **React Chart.js 2**: React wrapper for Chart.js

## Backend Technologies

### Core Framework
- **FastAPI**: Modern Python web framework
- **Python 3.10+**: Programming language
- **Uvicorn**: ASGI server
- **Gunicorn**: WSGI HTTP server

### AI/ML Libraries

#### Computer Vision
- **MediaPipe**: Face detection and tracking
- **OpenCV**: Image processing
- **Pillow (PIL)**: Image manipulation
- **Vision Transformer (ViT)**: Emotion recognition model

#### Natural Language Processing
- **Transformers (Hugging Face)**: BERT models
- **Whisper (OpenAI)**: Speech-to-text transcription
- **torch**: PyTorch for model inference

#### Audio Processing
- **librosa**: Audio feature extraction
- **soundfile**: Audio file I/O
- **numpy**: Numerical computing
- **scipy**: Scientific computing

#### Machine Learning
- **TensorFlow/Keras**: Deep learning framework
- **scikit-learn**: Machine learning utilities
- **pandas**: Data manipulation
- **numpy**: Numerical operations

### API & Web
- **FastAPI**: REST API framework
- **Pydantic**: Data validation
- **CORS Middleware**: Cross-origin resource sharing
- **Background Tasks**: Async processing

### File Processing
- **moviepy**: Video processing
- **ffmpeg-python**: Video/audio conversion
- **boto3**: AWS SDK for Python

## Infrastructure & Services

### Database
- **Firebase Firestore**: NoSQL document database
  - Real-time updates
  - Scalable architecture
  - Offline support

### Storage
- **AWS S3**: Object storage for videos
  - Private buckets
  - Presigned URLs
  - Lifecycle policies

### Authentication
- **Firebase Authentication**: User management
  - Email/password
  - JWT tokens
  - Session management

### Email Services
- **AWS SES**: Transactional emails
- **SendGrid**: Email delivery (alternative)

### Hosting & Deployment

#### Frontend
- **Vercel**: Next.js hosting
  - Edge network
  - Automatic deployments
  - Serverless functions

#### Backend
- **Fly.io**: Container hosting
  - Docker containers
  - Global distribution
- **Render**: Alternative hosting
  - Auto-scaling
  - Health checks

### Monitoring & Logging
- **Platform-native logging**: Vercel, Fly.io logs
- **Custom logging**: Application-level logs
- **Error tracking**: Built-in error handling

## Development Tools

### Version Control
- **Git**: Version control system
- **GitHub**: Code repository (private)

### Package Management
- **npm**: Node.js package manager
- **pip**: Python package manager

### Build Tools
- **Next.js Build**: Production builds
- **TypeScript Compiler**: Type checking
- **ESLint**: Code linting
- **PostCSS**: CSS processing

### Development Environment
- **Node.js**: JavaScript runtime
- **Python 3.10+**: Python runtime
- **Docker**: Containerization
- **VS Code**: Recommended IDE

## Security Technologies

### Encryption
- **HTTPS/TLS**: Encrypted connections
- **JWT**: Secure token authentication
- **AWS KMS**: Key management (if used)

### Security Headers
- **CORS**: Cross-origin protection
- **CSP**: Content Security Policy
- **XSS Protection**: Cross-site scripting prevention

## Third-Party Integrations

### Analytics
- **Google Analytics**: Web analytics (if implemented)
- **Custom Analytics**: Application-specific tracking

### Payment Processing
- **Stripe**: Payment gateway (planned)
- **PayPal**: Alternative payment (planned)

## Model Files & Assets

### AI Models
- **emotion_recognition_model.h5**: Audio emotion model
- **ViT models**: Vision Transformer weights
- **BERT models**: Text emotion models
- **Scalers & Pipelines**: Preprocessing models

### Static Assets
- **Images**: Logos, illustrations
- **Fonts**: Custom typography
- **Icons**: SVG icon sets

## Performance Optimizations

### Frontend
- **Code Splitting**: Next.js automatic splitting
- **Image Optimization**: Next.js Image component
- **Lazy Loading**: Component-level lazy loading
- **Caching**: Browser and CDN caching

### Backend
- **Async Processing**: Background tasks
- **Model Caching**: In-memory model storage
- **Connection Pooling**: Database connections
- **Parallel Processing**: Multi-threaded video processing

## Dependencies Summary

### Frontend Key Dependencies
```json
{
  "next": "14.2.4",
  "react": "^18",
  "typescript": "^5",
  "tailwindcss": "^3.4.1",
  "framer-motion": "^12.4.7",
  "firebase": "^11.0.1",
  "@aws-sdk/client-s3": "^3.734.0"
}
```

### Backend Key Dependencies
```txt
fastapi>=0.104.0
uvicorn>=0.24.0
tensorflow>=2.13.0
torch>=2.0.0
transformers>=4.30.0
mediapipe>=0.10.0
opencv-python>=4.8.0
librosa>=0.10.0
boto3>=1.28.0
firebase-admin>=6.2.0
```

## Browser Support

- **Chrome**: Latest 2 versions
- **Firefox**: Latest 2 versions
- **Safari**: Latest 2 versions
- **Edge**: Latest 2 versions
- **Mobile browsers**: iOS Safari, Chrome Mobile
