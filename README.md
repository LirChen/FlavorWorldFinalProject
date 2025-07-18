# FlavorWorldFinalProject:
#create .env file (PORT = 3000) \n
#change the IP adresses in the services to your IP address \n

In the server directory: \n
cd server \n
RUN npm install socket.io express mongoose cors multer dotenv \n
RUN node index.js \n

In the main directory: \n 
RUN npm install socket.io-client expo-modules-core expo-document-picker \n 
RUN npx expo start -c \n
