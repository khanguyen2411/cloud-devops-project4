FROM public.ecr.aws/docker/library/node:18.14.2-alpine3.17

ARG REACT_APP_MOVIE_API_URL
ENV REACT_APP_MOVIE_API_URL=${REACT_APP_MOVIE_API_URL}

WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install packages
RUN npm install

# Copy code
COPY . .

# Update caniuse-lite
RUN npx update-browserslist-db@latest --force

# Build the app without failing on linting warnings
RUN npm run build

# Expose the port used by the React app
EXPOSE 3000

# Install serve and start the React app
RUN npm install -g serve
CMD ["serve", "-s", "build"]
