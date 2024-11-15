
# **Backend Intern Assignment: Retail Pulse**

## **Description**
This project implements a system for receiving and scheduling jobs to process images using **Golang goroutines**. The system includes APIs for job submission and processing, database management using **GORM** for PostgreSQL, and robust error handling.

### **Key Components**
- **Entry Point**: The program starts with `main.go`.
- **API Implementation**: APIs are implemented using the `net/http` module (`routes.go`).
- **Job Handling**: Upon hitting the "Submit Job" API, a goroutine (`job.go`) is spawned to:
  - Download images from the provided URLs.
  - Calculate the perimeter of the images.
- **Database**:
  - **Job Table**: Contains `job_id` and its processing status.
  - **Image Table**: Stores metadata such as:
    - Image URL
    - Store ID
    - Perimeter
    - `error_message` in case of issues (e.g., network timeout, invalid URL).
  - Images are linked to jobs via a **foreign key** relationship.
- **Error Handling**: Comprehensive error handling is implemented throughout the codebase (`errors.go`).

---

## **Installation and Setup**

### **Prerequisites**
- Ensure **Go** is installed on your system.
- For Docker setup, install **Docker** and **Docker Compose**.

### **Local Setup**
1. Navigate to your `GOPATH` directory:
   ```bash
   cd $GOPATH
   mkdir -p src/github.com/charucjoshi
   cd src/github.com/charucjoshi
   ```
2. Clone the repository:
   ```bash
   git clone <repo-url>
   cd <repo>
   ```
3. Install dependencies:
   ```bash
   go mod download
   ```
4. Set up a PostgreSQL database using the credentials in `.env`.

5. Run the program:
   ```bash
   go run .
   ```
   Or build and execute:
   ```bash
   go build
   ./<binary>
   ```

### **Docker Setup**
1. Build and start the application using Docker Compose:
   ```bash
   docker-compose up -d --build
   ```
2. To bring the containers down:
   ```bash
   docker-compose down -v
   ```

---

## **Scope for Improvement**
While **goroutines** are efficient and lightweight for threading in Go, they may not always be reliable in complex scenarios. For a more scalable and robust solution, a **message broker** like **Redis** or **RabbitMQ** could be used. These tools:
- Schedule tasks in a **queue-based** manner.
- Provide greater resilience and failure tolerance.

However, due to time constraints, this enhancement was not implemented in the current version.

---

## **Future Enhancements**
- Replace goroutines with a task queue for job scheduling.
- Introduce additional monitoring and logging mechanisms for better observability.
- Add comprehensive unit and integration tests.

---

## **Work Environment**
- **Operating System**: WSL2 Ubuntu on Windows 11
- **Editor**: Visual Studio Code with the Go extension

---