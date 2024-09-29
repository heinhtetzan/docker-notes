Here's a guide on setting up WordPress and MySQL using Docker Compose. This method simplifies the process by defining all services and configurations in a single `docker-compose.yml` file, making it easier to manage and run.

### `docker-compose.yml`

Create a file named `docker-compose.yml` in your project directory and add the following content:

```yaml
version: '3.9'

services:
  db:
    image: mysql:5.7               # Use the MySQL 5.7 image
    container_name: my-mysql       # Name of the MySQL container
    environment:
      MYSQL_ROOT_PASSWORD: asdffdsa    # Set the root password
      MYSQL_DATABASE: wp                # Create a database named 'wp'
      MYSQL_USER: hhz                   # Create a MySQL user named 'hhz'
      MYSQL_PASSWORD: asdffdsa          # Set the password for the user
    ports:
      - "5500:3306"                    # Map port 5500 on the host to 3306 in the container
    volumes:
      - mysql_data:/var/lib/mysql      # Persist MySQL data using a volume

  wordpress:
    image: wordpress:latest          # Use the latest WordPress image
    container_name: my-wp            # Name of the WordPress container
    ports:
      - "8080:80"                    # Map port 8080 on the host to port 80 in the container
    environment:
      WORDPRESS_DB_HOST: db:3306     # Connect to the MySQL container
      WORDPRESS_DB_USER: hhz         # MySQL user created above
      WORDPRESS_DB_PASSWORD: asdffdsa # Password for the MySQL user
      WORDPRESS_DB_NAME: wp          # Name of the database
    depends_on:
      - db                          # Ensure the MySQL container starts first

volumes:
  mysql_data:
```

### Step-by-Step Commands

1. **Create and Start Containers**

   Run the following command in the directory where your `docker-compose.yml` file is located:

   ```bash
   docker-compose up -d
   ```

   This command will build and start both the WordPress and MySQL containers in detached mode.

2. **Stop and Remove Containers**

   To stop and remove the containers, networks, and volumes defined in the `docker-compose.yml` file:

   ```bash
   docker-compose down
   ```

3. **Check the Status of Running Containers**

   To view the status of the running containers:

   ```bash
   docker-compose ps
   ```

### Access WordPress

Once the containers are up and running, you can access WordPress at:

```
http://localhost:8080
```

### Key Points

- **`depends_on`**: Ensures the MySQL container starts before the WordPress container.
- **Volumes**: Data persistence is managed through Docker volumes, which prevent data loss when containers are stopped.
- **Environment Variables**: Used to configure the WordPress and MySQL containers.

This approach with Docker Compose simplifies managing and configuring your WordPress and MySQL setup, allowing for easy scaling and portability. Let me know if you need further adjustments or additional explanations!