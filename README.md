# streaming-05-smart-smoker
```markdown
streaming-05-start-smoker

Olakunle Alabi  
June 1, 2024  

 Project Goal

The goal of the project is to create a producer that processes and sends CSV data to RabbitMQ for a consumer.

 The Problem / Challenge To Solve

We want to stream information from a smart smoker. Read one value every half minute (sleep_secs = 30).

`smoker-temps.csv` has 4 columns:

1. **Time** = Date-time stamp for the sensor reading  
2. **Channel1** = Smoker Temp --> send to message queue "01-smoker"  
3. **Channel2** = Food A Temp --> send to message queue "02-food-A"  
4. **Channel3** = Food B Temp --> send to message queue "03-food-B"  

Requirements

- RabbitMQ Server running
- Pika installed in .venv
- Use Module 4 projects as examples

## Task 1. Create a Place to Work

1. In GitHub, create a new repo for your project - name it `streaming-05-smart-smoker`.
2. Add a `README.md` during the creation process. (If not, you can always add it later.)
3. Clone your repo down to your machine.
4. In VS Code, add a `.gitignore` (use one from an earlier module), start working on the `README.md`. Create it if you didn't earlier.
5. Add the CSV data file to your repo.
6. Create a file for your BBQ producer.

## Task 2. Design and Implement Your Producer

1. Implement your BBQ producer. More detailed help provided in links below.
2. Use the logic, approach, and structure from Module 4, version 2 and version 3. These provide a current and solid foundation for streaming analytics - modifying them to serve your purpose IS part of the assignment.
3. Do not start from scratch - do not search for code - do not use a notebook.
4. Use comments in the code and repo to explain your work.
5. Use docstring comments and add your name and date to your README and your code files.
6. Explain your project in the README. Include prerequisites and how to run your code.
7. Document your project works - display screenshots of your console and maybe the RabbitMQ console.
8. If you only have a producer, you won't have a consumer showing messages yet, so you'll need to be creative. We'll build the consumers next.

## Read

- To be guided through the producer design, read [Module 5.1 Guided Producer Design](https://nwmissouri.instructure.com/courses/60464/pages/module-5-dot-1-guided-producer-design?wrap=1)
- For a bit more guidance on the coding implementation, read [Module 5.2 Guided Producer Implementation](https://nwmissouri.instructure.com/courses/60464/pages/module-5-dot-2-guided-producer-implementation?wrap=1)

## Producer Code Setup

1. Import `pika`, `csv`, `sys`, and `webbrowser`.
2. Add `util_logger.py` file to the repository and initialize logging.
3. Create a function that offers to open RabbitMQ Admin site.
4. Write a function that connects to RabbitMQ, creates 3 queues, and deletes existing queues with the same name.
5. Create a function that establishes a path to the `smoker-temps.csv` and extracts the desired info from each row.
6. Create a `send_message` function that sends the message to the specified queue.

## Run the Code

### Create A Virtual Environment

1. Open a terminal window in VS Code.
2. Use the built-in Python utility `venv` to create a new virtual environment named `.venv` in the current directory.
    ```sh
    python3 -m venv .venv
    ```
3. Verify you get a new `.venv` directory in your project. We use `.venv` as the name to keep it away from our project files.

### Activate the Virtual Environment

1. In the same VS Code terminal window, activate the virtual environment.
    - On Linux/MacOS, run:
    ```sh
    source .venv/bin/activate
    ```
2. Verify you see the virtual environment name (.venv) in your terminal prompt.

### Start RabbitMQ Server

1. On a Mac terminal, start the RabbitMQ server.
    - On MacOS, run:
    ```sh
    brew services start rabbitmq
    ```

### Execute the Producer

1. Run the producer in the VS Code terminal.
    - Open the terminal in VS Code and run:
    ```sh
    python Bbq_producer.py
    ```
    to send the tasks to the RabbitMQ queue.
    
## Producer Image
```
