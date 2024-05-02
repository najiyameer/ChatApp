# ChatApp
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Chat App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    .app {
      max-width: 600px;
      margin: 20px auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    .chat-box {
      margin-bottom: 10px;
    }

    .user {
      font-weight: bold;
      color: #333;
    }

    .message {
      margin-left: 5px;
      color: #666;
    }

    input[type="text"] {
      width: calc(100% - 10px);
      padding: 5px;
      margin-top: 10px;
      border: 1px solid #ccc;
      border-radius: 3px;
    }
  </style>
</head>
<body>
  <div id="app">
    <div class="chat-box" v-for="message in messages" :key="message.id">
      <span class="user">{{ message.user }}:</span>
      <span class="message">{{ message.text }}</span>
    </div>
    <input type="text" v-model="newMessage" @keyup.enter="sendMessage" placeholder="Type your message...">
  </div>

  <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
  <script>
    new Vue({
      el: '#app',
      data: {
        messages: [],
        newMessage: ''
      },
      methods: {
        sendMessage() {
          if (this.newMessage.trim() !== '') {
            this.messages.push({
              id: Date.now(),
              user: 'Me',
              text: this.newMessage.trim()
            });
            this.newMessage = '';
          }
        }
      }
    });
  </script>
</body>
</html>
