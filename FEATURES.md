# Neurofy Features

## Core Features

### 🎭 Multimodal Emotion Analysis

#### Vision Analysis (Facial Expression)
- **Frame-by-frame processing** at 10 frames per second
- **MediaPipe face detection** for robust face tracking
- **Vision Transformer (ViT)** model for emotion recognition
- **Temporal smoothing** using Exponential Moving Average (EMA)
- **7 emotion categories**: Anger, Disgust, Fear, Joy, Neutral, Sadness, Surprise

#### Speech Analysis (Text Sentiment)
- **Whisper transcription** for accurate speech-to-text
- **BERT-based models** for text emotion analysis
- **Natural language processing** for sentiment detection
- **Context-aware analysis** of verbal responses

#### Tone Analysis (Audio Features)
- **Advanced audio feature extraction**:
  - Zero Crossing Rate (ZCR)
  - Chroma STFT
  - Mel-frequency Cepstral Coefficients (MFCC)
  - Root Mean Square (RMS) energy
  - Mel Spectrogram
- **CNN-based emotion model** for audio tone analysis
- **Real-time audio processing**

#### Combined Analysis
- **Weighted fusion** of all three modalities:
  - Vision: 40% weight
  - Speech: 35% weight
  - Tone: 25% weight
- **Comprehensive emotion profile** for each response

### 📊 Campaign Management

#### Campaign Creation
- Upload ad videos (MP4, AVI, MOV formats)
- Set campaign parameters:
  - Title and description
  - Participant limits
  - Video length limits (based on subscription)
- Automatic video processing and storage

#### Participant Management
- **Email invitations** with unique links
- **Participant tracking** and status monitoring
- **Response collection** interface
- **Real-time updates** on response status

#### Analytics Dashboard
- **Campaign overview** with key metrics
- **Individual response analysis**
- **Aggregate statistics**:
  - Average emotion scores
  - Emotion distribution charts
  - Response rate tracking
- **Export capabilities** (CSV, PDF)

### 🎥 Video Analysis

#### Direct Video Upload
- Upload videos for immediate analysis
- Support for multiple video formats
- Real-time processing status

#### Frame-by-Frame Analysis
- Detailed emotion tracking per frame
- Timestamp-based analysis
- Dominant emotion identification
- Confidence scores

#### Attractiveness Scoring
- Facial feature analysis
- Golden ratio calculations
- Symmetry measurements
- Comprehensive attractiveness metrics

#### Export Options
- CSV export with detailed frame data
- Summary reports
- Visualizations and charts

### 💼 Subscription Management

#### Subscription Tiers

**Starter (Free)**
- ≤ 30 seconds video length
- 1 participant per campaign
- Basic analytics
- Watermarked results

**Basic ($5/project)**
- ≤ 1 minute video length
- ≤ 10 participants
- Enhanced analytics
- No watermark

**Pro ($25/project)**
- ≤ 3 minutes video length
- ≤ 30 participants
- Full analytics suite
- Advanced AI features
- Export capabilities

**Premium ($50/project)**
- Unlimited video length
- Unlimited participants
- Priority processing
- Dedicated support
- Enterprise features

#### Usage Tracking
- Project usage monitoring
- Limit enforcement
- Upgrade prompts
- Billing integration

### 🔐 Security & Privacy

#### Authentication
- Firebase Authentication
- Email/password login
- Secure session management
- Password reset functionality

#### Data Protection
- Encrypted data transmission (HTTPS)
- Secure video storage (AWS S3)
- Private bucket access
- Participant data anonymization
- GDPR compliance

#### Access Control
- User-based campaign access
- Role-based permissions
- Secure API endpoints
- CORS protection

### 📧 Communication

#### Email System
- Automated invitation emails
- Customizable email templates
- Delivery tracking
- Bounce handling

#### Notifications
- Campaign status updates
- Processing completion alerts
- Subscription notifications
- System announcements

### 🎨 User Interface

#### Modern Design
- Responsive layout (mobile, tablet, desktop)
- Dark mode support
- Smooth animations (Framer Motion)
- Intuitive navigation

#### Interactive Components
- Real-time charts and graphs
- Video player with emotion overlay
- Drag-and-drop file uploads
- Progress indicators

#### Accessibility
- Keyboard navigation
- Screen reader support
- High contrast mode
- Responsive typography

## Advanced Features

### AI Recommendations
- Automated suggestions for ad improvements
- Pattern recognition across campaigns
- Best practice recommendations
- Performance optimization tips

### Comparative Analysis
- Side-by-side campaign comparison
- A/B testing support
- Version tracking
- Historical data analysis

### Real-time Processing
- Live analysis status updates
- Progress tracking
- Error handling and recovery
- Queue management

### Integration Capabilities
- API access for custom integrations
- Webhook support (planned)
- Export to external tools
- Data synchronization

## Future Roadmap

- [ ] Mobile native apps (iOS/Android)
- [ ] Advanced analytics dashboard
- [ ] Custom emotion models
- [ ] Multi-language support
- [ ] Team collaboration features
- [ ] White-label solutions
- [ ] API marketplace
- [ ] Machine learning model training interface
