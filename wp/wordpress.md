Here are all the Docker commands rewritten in a single line for each step. These commands can be copied and run sequentially.

### Step 1: Pull Docker Images

```
docker pull wordpress && docker pull mysql
```

### Step 2: Run the MySQL Container

```
docker run -d --name my-mysql -e MYSQL_ROOT_PASSWORD=asdffdsa -e MYSQL_DATABASE=wp -e MYSQL_USER=hhz -e MYSQL_PASSWORD=asdffdsa -p 5500:3306 -v mysql_data:/var/lib/mysql mysql
```

### Step 3: Run the WordPress Container Without Environment Variables

```
docker run -d --name my-wp -p 8080:80 wordpress
```

### Step 4: Manage Your Containers

- **Stop Containers:**

  ```
  docker stop my-wp my-mysql
  ```

- **Remove Containers:**

  ```
  docker rm my-wp my-mysql
  ```

- **Check Running Containers:**

  ```
  docker ps
  ```

These commands are now in a concise, one-line format for easy execution. Let me know if you need further adjustments!
