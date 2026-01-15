# Neurofy Architecture Documentation

## System Overview

Neurofy is built on a modern, scalable architecture that separates concerns between frontend, backend, and infrastructure services.

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Client Layer                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │
│  │   Web App    │  │  Mobile Web  │  │   Admin      │    │
│  │  (Next.js)   │  │  (Responsive)│  │  Dashboard   │    │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘    │
└─────────┼──────────────────┼──────────────────┼────────────┘
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

**API Endpoints**:
- `POST /process_review_video` - Process campaign response videos
- `POST /analyze_video_advanced` - Advanced video analysis
- `GET /campaigns` - Campaign management
- `POST /send_invitation` - Send participant invitations

### AI/ML Pipeline

#### 1. Vision Analysis (Facial Expression)
```
Video Input
    ↓
Frame Extraction (10 fps)
    ↓
MediaPipe Face Detection
    ↓
Face Cropping (Largest Face)
    ↓
ViT Model (Emotion Recognition)
    ↓
Temporal Smoothing (EMA)
    ↓
Emotion Scores (7 emotions)
```

#### 2. Speech Analysis (Text Sentiment)
```
Video Input
    ↓
Audio Extraction (WAV)
    ↓
Whisper Transcription
    ↓
Text Tokenization
    ↓
BERT-based Emotion Model
    ↓
Emotion Scores (7 emotions)
```

#### 3. Tone Analysis (Audio Features)
```
Video Input
    ↓
Audio Extraction (WAV)
    ↓
Feature Extraction (librosa)
    - ZCR, Chroma, MFCC, RMS, MelSpectrogram
    ↓
CNN-based Emotion Model
    ↓
Emotion Scores (7 emotions)
```

#### 4. Fusion
```
Vision (40%) + Speech (35%) + Tone (25%)
    ↓
Weighted Average
    ↓
Final Emotion Scores
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

## Database Schema

### Firebase Firestore Collections

**Campaigns**
```typescript
{
  id: string
  userId: string
  title: string
  videoUrl: string
  createdAt: timestamp
  status: 'active' | 'completed'
  participants: number
}
```

**Responses**
```typescript
{
  id: string
  campaignId: string
  participantId: string
  videoUrl: string
  emotions: {
    vision: EmotionScores
    speech: EmotionScores
    tone: EmotionScores
    combined: EmotionScores
  }
  timestamp: timestamp
}
```

**UserSubscriptions**
```typescript
{
  userId: string
  planId: string
  planName: string
  projectsUsed: number
  projectsLimit: number
  expiresAt: timestamp
}
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
- **Platform**: Fly.io / Render
- **Container**: Docker
- **Scaling**: Horizontal auto-scaling
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

## Scalability Considerations

- **Horizontal Scaling**: Stateless backend services
- **Database**: Firestore auto-scaling
- **Storage**: S3 unlimited capacity
- **Processing**: Queue-based video processing
- **Caching**: Multi-layer caching strategy

## Monitoring & Logging

- Application logs via platform services
- Error tracking and alerting
- Performance metrics
- User analytics
- API usage monitoring
