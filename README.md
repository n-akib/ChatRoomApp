# ChatRoomApp

A real-time chat application built with Java Spring Boot, WebSockets, and STOMP protocol. This application enables multiple users to communicate in real-time through a simple and intuitive web interface.

## 🚀 Features

- **Real-time messaging**: Instant message delivery using WebSockets and STOMP protocol
- **Simple user interface**: Clean and responsive design with Bootstrap 5
- **Multi-user support**: Multiple users can chat simultaneously
- **Auto-scroll**: Chat window automatically scrolls to show latest messages
- **SockJS fallback**: Ensures compatibility across different browsers
- **Lightweight**: Minimal dependencies and straightforward implementation

## 🛠️ Technologies Used

### Backend
- **Java** - Core programming language
- **Spring Boot** - Application framework
- **Spring WebSocket** - WebSocket support
- **STOMP Protocol** - Simple Text Oriented Messaging Protocol
- **Lombok** - Reduces boilerplate code

### Frontend
- **HTML5** - Markup structure
- **Bootstrap 5.3.7** - CSS framework for responsive design
- **JavaScript** - Client-side functionality
- **SockJS** - WebSocket fallback library
- **STOMP.js** - STOMP protocol client library

## 📋 Prerequisites

- Java 8 or higher
- Maven 3.6 or higher
- A modern web browser

## 🔧 Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/n-akib/ChatRoomApp.git
   cd ChatRoomApp
   ```

2. **Build the project**:
   ```bash
   mvn clean install
   ```

3. **Run the application**:
   ```bash
   mvn spring-boot:run
   ```

4. **Access the application**:
   Open your browser and navigate to `http://localhost:8080/chat`

## 🎮 How to Use

1. **Open the chat application** in your browser at `http://localhost:8080/chat`
2. **Enter your name** in the "Your name..." field
3. **Type your message** in the "Type a message..." field
4. **Click "Send"** or press Enter to send your message
5. **View messages** in real-time from all connected users in the chat window

## 🏗️ Project Structure

```
ChatRoomApp/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── chat/
│   │   │           └── app/
│   │   │               ├── AppApplication.java
│   │   │               ├── config/
│   │   │               │   └── WebSocketConfig.java
│   │   │               ├── controller/
│   │   │               │   └── ChatController.java
│   │   │               └── model/
│   │   │                   └── ChatMessage.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── templates/
│   │           └── chat.html
├── pom.xml
└── README.md
```

## 📝 Core Components

### 1. ChatMessage Model
```java
@Data
@NoArgsConstructor
public class ChatMessage {
    private Long id;
    private String sender;
    private String content;
}
```
- Simple POJO representing a chat message
- Uses Lombok for automatic getter/setter generation

### 2. WebSocket Configuration
```java
@Configuration
@EnableWebSocketMessageBroker
public class WebSocketConfig implements WebSocketMessageBrokerConfigurer
```
- **Endpoint**: `/chat` with SockJS fallback
- **Message Broker**: `/topic` for broadcasting messages
- **Application Prefix**: `/app` for client-to-server messages
- **Allowed Origins**: `http://localhost:8080`

### 3. Chat Controller
```java
@Controller
public class ChatController
```
- **Message Mapping**: `/sendMessage` for handling incoming messages
- **Send To**: `/topic/messages` for broadcasting to all subscribers
- **GET Mapping**: `/chat` serves the chat HTML page

### 4. Frontend Implementation
- **Connection**: Establishes WebSocket connection on page load
- **Message Display**: Real-time message rendering with sender identification
- **Auto-scroll**: Automatically scrolls to latest messages
- **Message Sending**: Handles user input and message transmission

## 🔧 Configuration Details

### WebSocket Endpoints
- **Connection Endpoint**: `/chat` - WebSocket handshake
- **Message Destination**: `/app/sendMessage` - Send messages
- **Subscription Topic**: `/topic/messages` - Receive messages

### Application Properties
```properties
spring.application.name=app
```

## 🌐 API Endpoints

### HTTP Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/chat` | Serves the chat application page |

### WebSocket Endpoints
| Destination | Type | Description |
|-------------|------|-------------|
| `/chat` | WebSocket | WebSocket connection endpoint |
| `/app/sendMessage` | STOMP | Send a chat message |
| `/topic/messages` | STOMP | Subscribe to receive messages |

## 🎨 User Interface

### Chat Window
- **Height**: 300px with auto-scroll
- **Border**: Rounded border with padding
- **Message Format**: "Sender: Message content"

### Input Fields
- **Sender Input**: User name field
- **Message Input**: Message content field
- **Send Button**: Submits the message

### Styling
- **Bootstrap 5.3.7** for responsive design
- **Container layout** with proper spacing
- **Form controls** with Bootstrap styling

## 🔄 Message Flow

1. **User enters name and message** → Frontend captures input
2. **Send button clicked** → JavaScript sends message via STOMP
3. **Message received by controller** → `@MessageMapping("/sendMessage")`
4. **Message broadcasted** → `@SendTo("/topic/messages")`
5. **All subscribers receive message** → Real-time display update

## 🚀 Deployment

### Local Development
```bash
mvn spring-boot:run
```
Access at: `http://localhost:8080/chat`

### Production Build
```bash
mvn clean package
java -jar target/app-0.0.1-SNAPSHOT.jar
```

## 🔍 Testing

1. **Open multiple browser tabs/windows** to `http://localhost:8080/chat`
2. **Enter different names** in each tab
3. **Send messages** from different tabs
4. **Verify real-time delivery** across all open instances

## 🛠️ Customization

### Adding Features
- **User authentication**: Integrate Spring Security
- **Message persistence**: Add database support
- **Private messaging**: Implement user-to-user messaging
- **File sharing**: Add file upload capability
- **Emoji support**: Integrate emoji picker

### Styling Modifications
- **Custom CSS**: Add your own styles to chat.html
- **Theme support**: Implement dark/light theme toggle
- **Message formatting**: Add rich text support

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**n-akib** - [GitHub Profile](https://github.com/n-akib)

## 🙏 Acknowledgments

- Spring Boot team for excellent WebSocket support
- Bootstrap team for the responsive CSS framework
- SockJS and STOMP.js for reliable WebSocket communication

---

**Start chatting in real-time! 💬**