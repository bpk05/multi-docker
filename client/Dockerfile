#Specify a base image for split build
From node:alpine as builder

#adding work dir
WORKDIR '/app'

#Install dependencies
COPY ./package.json ./

RUN npm install
COPY . .

RUN npm run build
#Default command

#CMD ["npm", "run", "start"]

#Specify a base image for 2nd phase build
From nginx
EXPOSE 3000
#adding below for making nginx to use 3000 at client
COPY ./nginx/default.conf /etc/ngnix/conf.d/default.conf

#Dumping the content created in previous stage
COPY --from=builder /app/build /usr/share/nginx/html