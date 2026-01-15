# Neurofy Architecture Documentation

## System Overview

Neurofy is built on a modern, scalable architecture that separates concerns between frontend, backend, and infrastructure services.

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Client Layer                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │
│  │   Web App    │  │  Mobile Web  │  │   Admin      │       │
│  │  (Next.js)   │  │  (Responsive)│  │  Dashboard   │       │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘       │
└─────────┼──────────────────┼──────────────────┼─────────────┘
          │                  │                  │
          └──────────────────┼──────────────────┘
                             │
          ┌──────────────────▼──────────────────┐
          │      API Gateway / Load Balancer     │
          └──────────────────┬──────────────────┘
                             │
          ┌──────────────────▼──────────────────┐
          │         FastAPI Backend             │
          │  ┌──────────────────────────────┐  │
          │  │  Emotion Analysis Service    │  │
          │  │  - Vision (ViT)              │  │
          │  │  - Speech (BERT)             │  │
          │  │  - Tone (CNN)                │  │
          │  └──────────────────────────────┘  │
          │  ┌──────────────────────────────┐  │
          │  │  Campaign Management Service │  │
          │  └──────────────────────────────┘  │
          │  ┌──────────────────────────────┐  │
          │  │  Video Processing Service    │  │
          │  └──────────────────────────────┘  │
          └──────────────────┬──────────────────┘
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
    ┌─────▼─────┐    ┌───────▼──────┐   ┌──────▼──────┐
    │ Firebase  │    │    AWS S3    │   │  AWS SES    │
    │ Firestore │    │   Storage    │   │   Email     │
    └───────────┘    └──────────────┘   └─────────────┘
```

## Component Details

### Frontend Architecture

**Framework**: Next.js 14 with App Router

```
frontend/
├── src/
│   ├── app/              # Next.js App Router pages
│   │   ├── page.tsx      # Landing page
│   │   ├── campaigns/    # Campaign management
│   │   ├── video-analysis/ # Video analysis
│   │   └── api/          # API routes
│   ├── components/       # React components
│   │   ├── LandingPage/ # Landing page components
│   │   ├── VideoAnalysis/ # Video analysis UI
│   │   └── ui/          # Reusable UI components
│   ├── hooks/           # Custom React hooks
│   ├── utils/           # Utility functions
│   └── firebase.js      # Firebase configuration
```

**Key Features**:
- Server-side rendering (SSR) for SEO
- Client-side routing with Next.js
- Real-time updates with Firebase listeners
- Responsive design with Tailwind CSS

### Backend Architecture

**Framework**: FastAPI (Python)

```
backend/
├── fastapi-app/
│   ├── fastAPI.py       # Main API server
│   ├── advanced_video_analysis.py  # Video analysis logic
│   ├── emotion_models/  # AI/ML models
│   └── utils/          # Helper functions
```

## Data Flow

### Campaign Creation Flow
```
User → Frontend → Firebase (Campaign Data)
                → AWS S3 (Video Upload)
                → Backend (Process Video)
                → Firebase (Analysis Results)
```

### Participant Response Flow
```
Email Invitation → Participant → Video Recording
                                    ↓
                              Upload to S3
                                    ↓
                              Backend Processing
                                    ↓
                              Firebase Storage
                                    ↓
                              Dashboard Update
```

## Security Architecture

- **Authentication**: Firebase Auth (JWT tokens)
- **Authorization**: Role-based access control
- **Data Encryption**: HTTPS/TLS for all communications
- **Storage Security**: AWS S3 with private buckets
- **API Security**: CORS whitelist, rate limiting

## Deployment Architecture

### Frontend
- **Platform**: Vercel
- **CDN**: Global edge network
- **Build**: Next.js static generation + SSR

### Backend
- **Platform**: Google Cloud Platform
- **Load Balancing**: Platform-managed

### Infrastructure
- **Database**: Firebase Firestore (NoSQL)
- **Storage**: AWS S3 (Object storage)
- **Email**: AWS SES / SendGrid
- **Monitoring**: Platform-native + custom logging

## Performance Optimizations

1. **Video Processing**: Parallel frame processing
2. **Model Loading**: Lazy loading of AI models
3. **Caching**: Firebase caching for frequently accessed data
4. **CDN**: Static assets served via CDN
5. **Database Indexing**: Optimized Firestore queries

## Monitoring & Logging

- Application logs via platform services
- Error tracking and alerting
- Performance metrics
- User analytics
- API usage monitoring
