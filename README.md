# FlavorWorldFinalProject:
#create .env file (PORT = 3000) ,
#change the IP adresses in the services to your IP address 

In the server directory: 
cd server ,
RUN npm install socket.io express mongoose cors multer dotenv ,
RUN node index.js 

In the main directory: 
RUN npm install socket.io-client expo-modules-core expo-document-picker , 
RUN npx expo start -c 
