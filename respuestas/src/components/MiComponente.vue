<template>
  <div class="chat-container w-full max-w-lg mx-auto bg-gray-100 shadow-lg rounded-lg">
    <div id="chat-container" class="flex flex-col h-full">
      <div class="chat-header flex items-center justify-between p-4 bg-blue-500 text-white">
        <p class="chat-title font-bold text-xl">Respuestas si o no</p>
        <button id="close-chat" class="close-btn text-white">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="icon w-6 h-6"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
      <div id="chatbox" class="chatbox flex-1 overflow-y-auto p-4 bg-white space-y-4">
        <!-- Mensajes renderizados dinámicamente -->
      </div>
      <div class="input-area flex p-4 border-t border-gray-300">
        <input
          id="user-input"
          type="text"
          placeholder="Type a message..."
          class="input-field flex-1 p-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
        />
        <button
          id="send-button"
          class="send-btn ml-2 px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600"
        >
          Send
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const chatbox = document.getElementById('chatbox')
    const sendButton = document.getElementById('send-button')
    const userInput = document.getElementById('user-input')

    sendButton.addEventListener('click', function () {
      const userMessage = userInput.value
      if (userMessage.trim() !== '') {
        addUserMessage(userMessage)
        respondToUser(userMessage)
        userInput.value = '' // Limpiar el campo de texto
      }
    })

    // Evento para enviar mensaje al presionar Enter
    userInput.addEventListener('keyup', function (event) {
      if (event.key === 'Enter') {
        const userMessage = userInput.value
        if (userMessage.trim() !== '') {
          addUserMessage(userMessage)
          respondToUser(userMessage)
          userInput.value = ''
        }
      }
    })

    // Función para añadir mensaje de usuario
    function addUserMessage(message) {
      const messageElement = document.createElement('div')
      messageElement.classList.add('message', 'right')
      messageElement.innerHTML = `<p class="bubble right-bubble">${message}</p>`
      chatbox.appendChild(messageElement)
      chatbox.scrollTop = chatbox.scrollHeight // Scroll automático hacia el último mensaje
    }

    // Función para generar respuesta aleatoria
    function respondToUser() {
      const responses = [
        {
          message: 'Yes',
          image: 'https://media.tenor.com/RrGds_6QluQAAAAC/si-aja-seguro.gif'
        },
        {
          message: 'No',
          image: 'https://media.tenor.co/images/8a464a72274f8ce16ac4773b349df9e4/raw'
        }
      ]

      // Escoge una respuesta aleatoria
      const randomResponse = responses[Math.floor(Math.random() * responses.length)]

      setTimeout(() => {
        const botMessage = document.createElement('div')
        botMessage.classList.add('message', 'left')
        botMessage.innerHTML = `
          <p class="bubble left-bubble">${randomResponse.message}</p>
          <img src="${randomResponse.image}" alt="${randomResponse.message} response" class="response-image" onload="this.style.display='block'" />
        `
        chatbox.appendChild(botMessage)
        chatbox.scrollTop = chatbox.scrollHeight
      }, 500)
    }
  }
}
</script>

<style scoped>
.chat-container {
  height: 500px;
  border-radius: 10px;
  background-color: #f9f9f9;
}

.chat-header {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}

.chatbox {
  padding: 10px;
  background-color: white;
  border-radius: 10px;
}

.message {
  display: flex;
  align-items: center;
}

.right {
  justify-content: flex-end;
}

.left {
  justify-content: flex-start;
}

.bubble {
  max-width: 75%;
  padding: 10px;
  border-radius: 20px;
  font-size: 14px;
}

.right-bubble {
  background-color: #d1f0ff;
  color: #333;
  border-bottom-right-radius: 0;
}

.left-bubble {
  background-color: #f0f0f0;
  color: #333;
  border-bottom-left-radius: 0;
}

.response-image {
  max-width: 150px;
  margin-top: 5px;
  border-radius: 10px;
}

.input-area {
  background-color: #f1f1f1;
}

.input-field {
  background-color: #fff;
  border-radius: 20px;
}

.send-btn {
  background-color: #4a90e2;
}

.send-btn:hover {
  background-color: #357abf;
}
</style>
