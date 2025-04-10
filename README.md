<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram-like Chat</title>
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <style>
        :root {
            --primary-color: #0088cc;
            --secondary-color: #f0f2f5;
            --text-color: #333;
            --text-secondary: #707579;
            --online-color: #00c853;
            --message-bg: #e3f2fd;
            --message-bg-out: #ffffff;
            --border-color: #eaeaea;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f5f5f5;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .chat-container {
            width: 100%;
            max-width: 900px;
            height: 90vh;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            display: flex;
            overflow: hidden;
        }

        /* Sidebar */
        .sidebar {
            width: 30%;
            background-color: var(--secondary-color);
            border-right: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .sidebar-header {
            padding: 15px;
            background-color: white;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .user-profile {
            display: flex;
            align-items: center;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: #ddd;
            margin-right: 10px;
            overflow: hidden;
        }

        .user-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .user-name {
            font-weight: 600;
        }

        .sidebar-icons {
            display: flex;
            gap: 15px;
            color: var(--text-secondary);
        }

        .search-bar {
            padding: 10px;
            background-color: white;
            border-bottom: 1px solid var(--border-color);
        }

        .search-bar input {
            width: 100%;
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            background-color: var(--secondary-color);
            font-size: 14px;
        }

        .chat-list {
            flex: 1;
            overflow-y: auto;
        }

        .chat-item {
            padding: 12px 15px;
            border-bottom: 1px solid var(--border-color);
            cursor: pointer;
            display: flex;
            align-items: center;
            transition: background-color 0.2s;
        }

        .chat-item:hover {
            background-color: #f5f5f5;
        }

        .chat-item.active {
            background-color: var(--message-bg);
        }

        .chat-avatar {
            position: relative;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: #ddd;
            margin-right: 12px;
            overflow: hidden;
        }

        .chat-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .online-status {
            position: absolute;
            bottom: 0;
            right: 0;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: var(--online-color);
            border: 2px solid white;
        }

        .chat-info {
            flex: 1;
            min-width: 0;
        }

        .chat-name {
            font-weight: 600;
            margin-bottom: 4px;
            display: flex;
            justify-content: space-between;
        }

        .chat-time {
            font-size: 12px;
            color: var(--text-secondary);
            white-space: nowrap;
        }

        .chat-preview {
            font-size: 14px;
            color: var(--text-secondary);
            display: flex;
            justify-content: space-between;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .typing-indicator {
            color: var(--primary-color);
            font-style: italic;
            font-size: 12px;
        }

        /* Chat area */
        .chat-area {
            flex: 1;
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .chat-header {
            padding: 15px;
            background-color: white;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            align-items: center;
        }

        .chat-header-info {
            margin-left: 12px;
            flex: 1;
        }

        .chat-header-name {
            font-weight: 600;
            display: flex;
            align-items: center;
        }

        .chat-header-status {
            font-size: 13px;
            color: var(--text-secondary);
            display: flex;
            align-items: center;
        }

        .chat-header-status .online-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: var(--online-color);
            margin-right: 5px;
        }

        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            background-color: #e6ebee;
            background-image: url('https://web.telegram.org/img/pattern.png');
            background-attachment: fixed;
        }

        .message {
            max-width: 70%;
            margin-bottom: 10px;
            padding: 8px 12px;
            border-radius: 8px;
            position: relative;
            word-wrap: break-word;
            box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
        }

        .received {
            align-self: flex-start;
            background-color: white;
            border-top-left-radius: 0;
        }

        .sent {
            align-self: flex-end;
            background-color: var(--message-bg);
            border-top-right-radius: 0;
        }

        .message-time {
            font-size: 11px;
            color: var(--text-secondary);
            text-align: right;
            margin-top: 4px;
            display: flex;
            justify-content: flex-end;
            align-items: center;
        }

        .message-actions {
            position: absolute;
            right: 5px;
            top: 5px;
            display: none;
            background-color: rgba(0, 0, 0, 0.1);
            border-radius: 4px;
            padding: 2px;
        }

        .message:hover .message-actions {
            display: flex;
        }

        .message-action {
            padding: 2px 5px;
            cursor: pointer;
            color: var(--text-secondary);
            font-size: 12px;
        }

        .message-action:hover {
            color: var(--primary-color);
        }

        .chat-input-container {
            padding: 10px 15px;
            background-color: white;
            border-top: 1px solid var(--border-color);
            display: flex;
            align-items: center;
        }

        .input-tools {
            display: flex;
            align-items: center;
            margin-right: 10px;
        }

        .tool-button {
            font-size: 20px;
            color: var(--text-secondary);
            margin: 0 5px;
            cursor: pointer;
            transition: color 0.2s;
        }

        .tool-button:hover {
            color: var(--primary-color);
        }

        .record-button {
            color: #f44336;
            display: none;
        }

        .input-wrapper {
            flex: 1;
            display: flex;
            align-items: center;
            background-color: var(--secondary-color);
            border-radius: 20px;
            padding: 8px 15px;
        }

        .chat-input {
            flex: 1;
            border: none;
            outline: none;
            background: transparent;
            font-size: 15px;
            max-height: 100px;
            resize: none;
            padding: 5px 0;
        }

        .send-button {
            font-size: 20px;
            color: var(--primary-color);
            margin-left: 10px;
            cursor: pointer;
            display: none;
        }

        /* Auth modal */
        .auth-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .auth-container {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            width: 100%;
            max-width: 400px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .auth-title {
            font-size: 24px;
            margin-bottom: 20px;
            text-align: center;
            color: var(--primary-color);
        }

        .auth-input {
            width: 100%;
            padding: 12px 15px;
            margin-bottom: 15px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 16px;
        }

        .auth-button {
            width: 100%;
            padding: 12px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .auth-button:hover {
            background-color: #0077b3;
        }

        /* Recording indicator */
        .recording-indicator {
            position: fixed;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 10px 20px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            display: none;
        }

        .recording-dot {
            width: 10px;
            height: 10px;
            background-color: #f44336;
            border-radius: 50%;
            margin-right: 10px;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.3; }
            100% { opacity: 1; }
        }

        /* Media queries */
        @media (max-width: 768px) {
            .chat-container {
                height: 100vh;
                border-radius: 0;
            }
            .sidebar {
                width: 100%;
                display: none;
            }
            .sidebar.active {
                display: flex;
            }
            .chat-area {
                display: none;
            }
            .chat-area.active {
                display: flex;
            }
        }
    </style>
</head>
<body>
    <!-- Auth Modal -->
    <div class="auth-modal" id="authModal">
        <div class="auth-container">
            <h2 class="auth-title">Enter Your Name</h2>
            <input type="text" class="auth-input" id="usernameInput" placeholder="Your name" autofocus>
            <button class="auth-button" id="authButton">Continue</button>
        </div>
    </div>

    <!-- Recording Indicator -->
    <div class="recording-indicator" id="recordingIndicator">
        <div class="recording-dot"></div>
        <span>Recording...</span>
    </div>

    <!-- Chat Container -->
    <div class="chat-container" id="mainApp" style="display: none;">
        <!-- Sidebar -->
        <div class="sidebar" id="sidebar">
            <div class="sidebar-header">
                <div class="user-profile">
                    <div class="user-avatar" id="userAvatar">
                        <img id="userAvatarImg" src="" alt="User">
                    </div>
                    <div class="user-name" id="sidebarUserName"></div>
                </div>
                <div class="sidebar-icons">
                    <span>🔍</span>
                    <span>⋮</span>
                </div>
            </div>
            <div class="search-bar">
                <input type="text" placeholder="Search">
            </div>
            <div class="chat-list" id="chatList">
                <!-- Chats will be loaded here -->
            </div>
        </div>

        <!-- Chat Area -->
        <div class="chat-area" id="chatArea">
            <div class="chat-header">
                <div class="user-avatar">
                    <img id="chatAvatar" src="https://randomuser.me/api/portraits/men/1.jpg" alt="Chat">
                    <div class="online-status" id="onlineStatus"></div>
                </div>
                <div class="chat-header-info">
                    <div class="chat-header-name">
                        <span id="chatName">Telegram Chat</span>
                    </div>
                    <div class="chat-header-status">
                        <div class="online-dot" id="statusDot"></div>
                        <span id="statusText">online</span>
                        <span id="typingIndicator" class="typing-indicator"></span>
                    </div>
                </div>
            </div>
            <div class="chat-messages" id="chatMessages">
                <!-- Messages will be loaded here -->
            </div>
            <div class="chat-input-container">
                <div class="input-tools">
                    <div class="tool-button" id="attachButton">📎</div>
                    <div class="tool-button record-button" id="recordButton">🎙️</div>
                </div>
                <div class="input-wrapper">
                    <textarea class="chat-input" id="messageInput" placeholder="Write a message..." rows="1"></textarea>
                </div>
                <div class="send-button" id="sendButton">➤</div>
            </div>
        </div>
    </div>

    <script>
        // Supabase configuration - USING YOUR CREDENTIALS
        const SUPABASE_URL = 'https://vcycthqovwhyyhorsvnf.supabase.co';
        const SUPABASE_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZjeWN0aHFvdndoeXlob3Jzdm5mIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDQzMjEwNDIsImV4cCI6MjA1OTg5NzA0Mn0.qSi4C05196OxQIQdcyuKmh4FFZCnKKxxQKQJOYlmOvs';
        
        const supabase = supabase.createClient(SUPABASE_URL, SUPABASE_KEY);

        // DOM elements
        const authModal = document.getElementById('authModal');
        const usernameInput = document.getElementById('usernameInput');
        const authButton = document.getElementById('authButton');
        const mainApp = document.getElementById('mainApp');
        const userAvatarImg = document.getElementById('userAvatarImg');
        const sidebarUserName = document.getElementById('sidebarUserName');
        const chatList = document.getElementById('chatList');
        const chatMessages = document.getElementById('chatMessages');
        const messageInput = document.getElementById('messageInput');
        const sendButton = document.getElementById('sendButton');
        const recordButton = document.getElementById('recordButton');
        const attachButton = document.getElementById('attachButton');
        const recordingIndicator = document.getElementById('recordingIndicator');
        const chatName = document.getElementById('chatName');
        const statusText = document.getElementById('statusText');
        const statusDot = document.getElementById('statusDot');
        const typingIndicator = document.getElementById('typingIndicator');
        const onlineStatus = document.getElementById('onlineStatus');

        // App state
        let currentUser = null;
        let currentChat = null;
        let isRecording = false;
        let mediaRecorder = null;
        let audioChunks = [];
        let typingTimeout = null;
        let onlineInterval = null;

        // Initialize the app
        async function initApp() {
            // Check if user exists in localStorage
            const savedUser = localStorage.getItem('telegramChatUser');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                authModal.style.display = 'none';
                mainApp.style.display = 'flex';
                setupUser();
                setupChat();
            } else {
                authModal.style.display = 'flex';
            }

            // Set up event listeners
            setupEventListeners();
        }

        // Set up user interface
        function setupUser() {
            // Set user avatar and name
            const avatarUrl = `https://ui-avatars.com/api/?name=${encodeURIComponent(currentUser.name)}&background=random`;
            userAvatarImg.src = avatarUrl;
            sidebarUserName.textContent = currentUser.name;

            // Set up online status
            updateOnlineStatus(true);
            onlineInterval = setInterval(() => updateOnlineStatus(true), 30000); // Update every 30 seconds
        }

        // Set up chat interface
        async function setupChat() {
            // For demo purposes, we'll use a single chat
            currentChat = {
                id: 'global',
                name: 'Global Chat',
                avatar: 'https://randomuser.me/api/portraits/men/1.jpg',
                isOnline: true
            };

            chatName.textContent = currentChat.name;
            chatAvatar.src = currentChat.avatar;
            updateChatStatus(currentChat.isOnline);

            // Load messages
            await loadMessages();

            // Subscribe to real-time updates
            subscribeToRealtime();
        }

        // Set up event listeners
        function setupEventListeners() {
            // Auth modal
            authButton.addEventListener('click', handleAuth);
            usernameInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') handleAuth();
            });

            // Message input
            messageInput.addEventListener('input', handleInput);
            messageInput.addEventListener('keydown', (e) => {
                if (e.key === 'Enter' && !e.shiftKey) {
                    e.preventDefault();
                    sendMessage();
                }
            });

            // Send button
            sendButton.addEventListener('click', sendMessage);

            // Record button
            recordButton.addEventListener('mousedown', startRecording);
            recordButton.addEventListener('mouseup', stopRecording);
            recordButton.addEventListener('mouseleave', stopRecording);

            // Attach button
            attachButton.addEventListener('click', () => {
                alert('File attachment functionality would be implemented here');
            });

            // Auto-resize textarea
            messageInput.addEventListener('input', () => {
                messageInput.style.height = 'auto';
                messageInput.style.height = (messageInput.scrollHeight) + 'px';
            });
        }

        // Handle authentication
        async function handleAuth() {
            const username = usernameInput.value.trim();
            if (!username) return;

            try {
                // Create user in Supabase
                const { data, error } = await supabase
                    .from('users')
                    .upsert({
                        name: username,
                        last_online: new Date().toISOString(),
                        is_online: true
                    }, { onConflict: 'name' })
                    .select()
                    .single();

                if (error) throw error;

                currentUser = {
                    id: data.id,
                    name: data.name,
                    isOnline: true
                };

                // Save user to localStorage
                localStorage.setItem('telegramChatUser', JSON.stringify(currentUser));

                // Hide auth modal and show main app
                authModal.style.display = 'none';
                mainApp.style.display = 'flex';
                
                // Setup user and chat
                setupUser();
                setupChat();
            } catch (error) {
                console.error('Authentication error:', error);
                alert('Failed to authenticate. Please try again.');
            }
        }

        // Handle input changes (for typing indicator)
        function handleInput() {
            if (messageInput.value.trim()) {
                sendButton.style.display = 'block';
                recordButton.style.display = 'none';
            } else {
                sendButton.style.display = 'none';
                recordButton.style.display = 'block';
            }

            // Send typing indicator
            sendTypingIndicator(true);

            // Clear previous timeout
            if (typingTimeout) clearTimeout(typingTimeout);

            // Set timeout to stop typing indicator after 3 seconds
            typingTimeout = setTimeout(() => {
                sendTypingIndicator(false);
            }, 3000);
        }

        // Send typing indicator
        async function sendTypingIndicator(isTyping) {
            try {
                await supabase
                    .from('typing_indicators')
                    .upsert({
                        user_id: currentUser.id,
                        chat_id: currentChat.id,
                        is_typing: isTyping,
                        timestamp: new Date().toISOString()
                    });
            } catch (error) {
                console.error('Error sending typing indicator:', error);
            }
        }

        // Load messages
        async function loadMessages() {
            try {
                const { data: messages, error } = await supabase
                    .from('messages')
                    .select('*')
                    .eq('chat_id', currentChat.id)
                    .order('created_at', { ascending: true });

                if (error) throw error;

                renderMessages(messages);
            } catch (error) {
                console.error('Error loading messages:', error);
            }
        }

        // Render messages
        function renderMessages(messages) {
            chatMessages.innerHTML = '';

            if (!messages || messages.length === 0) {
                const emptyMessage = document.createElement('div');
                emptyMessage.className = 'message received';
                emptyMessage.style.alignSelf = 'center';
                emptyMessage.style.backgroundColor = 'transparent';
                emptyMessage.style.boxShadow = 'none';
                emptyMessage.style.textAlign = 'center';
                emptyMessage.style.color = 'var(--text-secondary)';
                emptyMessage.innerHTML = '<div>No messages yet. Start the conversation!</div>';
                chatMessages.appendChild(emptyMessage);
                return;
            }

            messages.forEach(message => {
                const isCurrentUser = message.user_id === currentUser.id;
                const messageDiv = document.createElement('div');
                messageDiv.className = `message ${isCurrentUser ? 'sent' : 'received'}`;
                
                // Format time
                const time = new Date(message.created_at).toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });

                messageDiv.innerHTML = `
                    <div class="message-text">${message.text}</div>
                    <div class="message-time">
                        ${time}
                        ${isCurrentUser ? `
                            <span class="message-actions">
                                <span class="message-action edit-message" data-id="${message.id}">✏️</span>
                                <span class="message-action delete-message" data-id="${message.id}">🗑️</span>
                            </span>
                        ` : ''}
                    </div>
                `;
                chatMessages.appendChild(messageDiv);
            });

            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;

            // Add event listeners for message actions
            document.querySelectorAll('.edit-message').forEach(btn => {
                btn.addEventListener('click', (e) => editMessage(e.target.dataset.id));
            });

            document.querySelectorAll('.delete-message').forEach(btn => {
                btn.addEventListener('click', (e) => deleteMessage(e.target.dataset.id));
            });
        }

        // Send message
        async function sendMessage() {
            const text = messageInput.value.trim();
            if (!text) return;

            try {
                // Create message in Supabase
                const { data, error } = await supabase
                    .from('messages')
                    .insert([
                        {
                            chat_id: currentChat.id,
                            user_id: currentUser.id,
                            text: text,
                            is_edited: false
                        }
                    ])
                    .select();

                if (error) throw error;

                // Clear input
                messageInput.value = '';
                messageInput.style.height = 'auto';
                sendButton.style.display = 'none';
                recordButton.style.display = 'block';

                // Stop typing indicator
                sendTypingIndicator(false);
            } catch (error) {
                console.error('Error sending message:', error);
                alert('Failed to send message. Please try again.');
            }
        }

        // Edit message
        async function editMessage(messageId) {
            const message = messages.find(m => m.id === messageId);
            if (!message) return;

            const messageText = prompt('Edit your message:', message.text);
            if (!messageText) return;

            try {
                const { error } = await supabase
                    .from('messages')
                    .update({
                        text: messageText,
                        is_edited: true,
                        updated_at: new Date().toISOString()
                    })
                    .eq('id', messageId);

                if (error) throw error;
            } catch (error) {
                console.error('Error editing message:', error);
                alert('Failed to edit message. Please try again.');
            }
        }

        // Delete message
        async function deleteMessage(messageId) {
            if (!confirm('Are you sure you want to delete this message?')) return;

            try {
                const { error } = await supabase
                    .from('messages')
                    .delete()
                    .eq('id', messageId);

                if (error) throw error;
            } catch (error) {
                console.error('Error deleting message:', error);
                alert('Failed to delete message. Please try again.');
            }
        }

        // Start recording
        async function startRecording() {
            try {
                isRecording = true;
                recordingIndicator.style.display = 'flex';
                
                const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
                mediaRecorder = new MediaRecorder(stream);
                audioChunks = [];

                mediaRecorder.ondataavailable = (e) => {
                    if (e.data.size > 0) {
                        audioChunks.push(e.data);
                    }
                };

                mediaRecorder.onstop = async () => {
                    const audioBlob = new Blob(audioChunks, { type: 'audio/webm' });
                    alert('Audio recording complete. In a real app, this would be sent to Supabase Storage.');
                };

                mediaRecorder.start();
            } catch (error) {
                console.error('Error starting recording:', error);
                isRecording = false;
                recordingIndicator.style.display = 'none';
                alert('Microphone access denied or not available.');
            }
        }

        // Stop recording
        function stopRecording() {
            if (!isRecording) return;
            
            isRecording = false;
            recordingIndicator.style.display = 'none';
            
            if (mediaRecorder && mediaRecorder.state !== 'inactive') {
                mediaRecorder.stop();
                mediaRecorder.stream.getTracks().forEach(track => track.stop());
            }
        }

        // Update online status
        async function updateOnlineStatus(isOnline) {
            if (!currentUser) return;
            
            currentUser.isOnline = isOnline;
            
            try {
                await supabase
                    .from('users')
                    .update({
                        is_online: isOnline,
                        last_online: new Date().toISOString()
                    })
                    .eq('id', currentUser.id);
            } catch (error) {
                console.error('Error updating online status:', error);
            }
        }

        // Update chat status
        function updateChatStatus(isOnline) {
            if (isOnline) {
                statusText.textContent = 'online';
                statusDot.style.backgroundColor = 'var(--online-color)';
                onlineStatus.style.display = 'block';
            } else {
                statusText.textContent = 'last seen recently';
                statusDot.style.backgroundColor = 'transparent';
                onlineStatus.style.display = 'none';
            }
        }

        // Subscribe to real-time updates
        function subscribeToRealtime() {
            // Messages
            supabase
                .channel('messages')
                .on(
                    'postgres_changes',
                    { event: '*', schema: 'public', table: 'messages' },
                    (payload) => {
                        if (payload.new.chat_id === currentChat.id) {
                            loadMessages();
                        }
                    }
                )
                .subscribe();

            // Typing indicators
            supabase
                .channel('typing')
                .on(
                    'postgres_changes',
                    { event: '*', schema: 'public', table: 'typing_indicators' },
                    (payload) => {
                        if (payload.new.chat_id === currentChat.id && payload.new.user_id !== currentUser.id) {
                            if (payload.new.is_typing) {
                                typingIndicator.textContent = 'typing...';
                            } else {
                                typingIndicator.textContent = '';
                            }
                        }
                    }
                )
                .subscribe();

            // Online status
            supabase
                .channel('online')
                .on(
                    'postgres_changes',
                    { event: '*', schema: 'public', table: 'users' },
                    (payload) => {
                        if (payload.new.id !== currentUser.id) {
                            updateChatStatus(payload.new.is_online);
                        }
                    }
                )
                .subscribe();
        }

        // Initialize the app when DOM is loaded
        document.addEventListener('DOMContentLoaded', initApp);

        // Update online status when window is focused/blurred
        window.addEventListener('focus', () => updateOnlineStatus(true));
        window.addEventListener('blur', () => updateOnlineStatus(false));

        // Clean up when page is unloaded
        window.addEventListener('beforeunload', () => {
            if (currentUser) {
                updateOnlineStatus(false);
                clearInterval(onlineInterval);
            }
        });
    </script>
</body>
</html>
