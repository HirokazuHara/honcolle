FROM node:24-alpine

WORKDIR /app

RUN npm install -g aws-cdk

COPY package*.json ./
RUN npm install

COPY . .

CMD ["sh"]