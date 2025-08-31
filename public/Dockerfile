FROM node:slim AS builder

WORKDIR /public

COPY . /public

RUN npm install

ENV REACT_APP_LOCALHOST_KEY="chat-app-current-user"

RUN npm run build

# Use the official httpd image as a base
FROM httpd
# Copy the React BUILD FILES (not just index.html) to httpd directory
COPY --from=builder /public/build/ /usr/local/apache2/htdocs/
# Expose port 80 for Apache
EXPOSE 80
