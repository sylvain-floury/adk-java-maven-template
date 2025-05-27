# Template project for building Java agents with ADK

This GitHub repository is a project template to get started creating your first 
agent with [ADK](https://google.github.io/adk-docs/) for Java, the open source
Agent Development Kit, and building with [Maven](https://maven.apache.org).

![](https://google.github.io/adk-docs/assets/agent-development-kit.png)

# Instructions

The following screenshot of the GitHub interface shows how you can use this template project to get started:

![](use-template.png)

Check out the GitHub [documentation](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)
about forking and cloning template projects.

> [!TIP]
> Be sure to read the [ADK documentation](https://google.github.io/adk-docs/get-started/quickstart/#set-up-the-model) 
> to better understand how the framework works.

# Setup

To use Gemini (or other supported models), you must set up the right environment variables for the model to be properly configured.

Set up the following environment variables:

```shell
export GOOGLE_API_KEY="PASTE_YOUR_ACTUAL_API_KEY_HERE"
export GOOGLE_GENAI_USE_VERTEXAI=FALSE
```

> [!TIP]
> You can get an API key in [Google AI Studio](https://aistudio.google.com/apikey).

> [!IMPORTANT]
> Be sure to replace `"PASTE_YOUR_ACTUAL_API_KEY_HERE"` above, with the value of the key.

# Running the agent

There are two options to run your agent: 
* from the command-line
* using the ADK Dev UI

## Running the agent from the command-line

Run the following Maven command:

```shell
mvn compile exec:java -Dexec.mainClass="com.example.agent.HelloWeatherAgent"
```

The `HelloWeatherAgent` class is a simple agent configured with one tool to request a canned weather forecast from any city.
When running the above command, you should see a similar output like the one below.
Type `quit` to exit the agent conversation.

```
[INFO] Scanning for projects...
[INFO] 
[INFO] --------------------< com.example.agent:adk-agents >--------------------
[INFO] Building adk-agents 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ adk-agents ---
[INFO] skip non existing resourceDirectory /Users/adkuser/projects/adk-java-maven-template/src/main/resources
[INFO] 
[INFO] --- compiler:3.13.0:compile (default-compile) @ adk-agents ---
[INFO] Recompiling the module because of changed source code.
[INFO] Compiling 1 source file with javac [debug target 17] to target/classes
[WARNING] system modules path not set in conjunction with -source 17
[INFO] Annotation processing is enabled because one or more processors were found
  on the class path. A future release of javac may disable annotation processing
  unless at least one processor is specified by name (-processor), or a search
  path is specified (--processor-path, --processor-module-path), or annotation
  processing is enabled explicitly (-proc:only, -proc:full).
  Use -Xlint:-options to suppress this message.
  Use -proc:none to disable annotation processing.
[INFO] 
[INFO] --- exec:3.5.0:java (default-cli) @ adk-agents ---

You > hi

Agent > Hello World


You > What's the weather in Paris?

Agent > The weather in Paris is: Sunny day, clear blue sky, temperature up to 24°C.


You > quit
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  01:46 min
[INFO] Finished at: 2025-05-27T11:07:54+02:00
[INFO] ------------------------------------------------------------------------
```

## Running the agent from the Dev UI

The Dev UI offers a useful chat interface to interact with your agent.
Run the command below to launch it, and open a browser at `http://localhost:8080/`.

```shell
mvn compile exec:java -Dexec.mainClass="com.google.adk.web.AdkWebServer" -Dexec.classpathScope="compile"
```

In your browser, you can select the agent in the top left-hand corner and chat with it in the main chat space.
In the left panel, you can explore the various events, including function calls, LLM requests, and responses, 
to understand what happens when a user converses with the agent.

Here's a screenshot of the Dev UI in action for your `HelloWeatherAgent` agent:

![](adk-dev-ui.png)

---

> [!NOTE]  
> This template project is not an official Google project 