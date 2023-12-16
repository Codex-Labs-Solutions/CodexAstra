# CodexAstra
CodexAstra is a Visual Studio Extension designed to enhance your coding experience through AI-assisted interactions. Engage in intelligent conversations with AI agents that provide real-time assistance directly within your IDE.

## Features
- **AI-Powered Chat**: Interact with AI agents to gain insight and assistance with your coding tasks.
- **Agent-Based Support**: Leverage a variety of agents, each specialized in different aspects of software development.
- **Visual Studio Integration**: Enjoy a seamless experience that brings AI capabilities right into your development workflow.
- **Bring your own deployment** No data leaves your Azure AI instance.
  
## Getting Started
To start using CodexAstra, follow these simple installation steps:

1. Ensure you have Visual Studio installed on your machine.
2. Download `CodexAstra.vsix` from the latest release.
3. Double-click the downloaded file to install the extension in Visual Studio.

If you're updating the extension remember to uninstall it from Visual Studio before you try to install a newer version

Once installed, open Visual Studio and you’ll find CodexAstra in the toolbar:
- Find the window under View -> Other Windows -> Codex Astra (or Ctrl+Q -> "Codex Astra")
- Configure your settings by clicking the settings icon next to the title

Click new chat to start a coding related chat or the dropdown for specific tasks.

### Daily Usage

Codex Astra is designed to streamline your development workflow by facilitating an interactive and productive dialogue with your codebase and development environment. Below are common daily usage scenarios that describe how to interact with and leverage the capabilities of Codex Astra effectively.

#### Get Work Item Details
When you start your day, you might want to get the details of a specific work item from Azure DevOps to prioritize tasks. Simply ask Codex Astra for the work item details:

- Use a prompt like "Get details for work item #12345."
- Codex Astra will fetch all the relevant details, facilitating your planning for the day.

#### Retrieve Existing Code
Before making changes, you may need to review existing code. Codex Astra can help by locating the code associated with a specific class or method:

- Phrase your request as "Show me the code for the `PaymentProcessor` class."
- Codex Astra will use its code search function to retrieve the source code, enabling you to proceed with informed changes.

#### Implement Changes
Once you've reviewed the work items and existing code, you might want Codex Astra to assist with implementing changes:

- Prompt it with "Implement a new method in `PaymentProcessor` for transaction validation."
- Codex Astra can draft code snippets or offer suggestions for the best practices to follow.

#### Work Iteratively
Development is an iterative process. Codex Astra supports this by enabling you to refine solutions through continuous interaction:

- Engage in a dialogue, refining the prompts based on previous outputs, like "Refine the validation method to include currency check."
- Iterate with Codex Astra until you reach a satisfactory solution.

#### Copy/Paste Answers
Once you're happy with the suggestions or code presented by Codex Astra:

- Copy the relevant outputs directly from the interface.
- Paste and integrate them into your project files or use them as a reference for manual coding.

#### Generate Commit Message
Good commit messages are crucial for maintainable version control history. Codex Astra can help generate meaningful commit messages based on the task info and the changes made:

- Instruct it with "Create a commit message for the changes made in `PaymentProcessor` based on task #12345."
- Use the generated message to commit your changes, ensuring your commit logs are informative and traceable to specific work items.

#### Best Practices
To make the most of your day with Codex Astra, here are some best practices:

- **Be Specific**: The more specific you are with your prompts, the more accurate and relevant Codex Astra's responses will be.
- **Follow Patterns**: Establish a pattern of prompts for common tasks, which can save you time and help standardize your interactions with Codex Astra.
- **Review and Adapt**: Always review Codex Astra’s output for accuracy and adapt it to fit the context of your project.
- **Automate When Possible**: Take advantage of Codex Astra's functions to automate repetitive tasks like code refactoring or fetching work item details.

By incorporating these steps into your daily routine, you'll enhance your productivity, reduce manual overhead, and make your development process more efficient and enjoyable. Codex Astra is here to help you every step of the way, from planning to coding to documentation.
### Technical Usage
#### Function Interaction Guide Using Natural Language Prompts

Interacting with CodexAstra functions can be done using specific language cues. The following table outlines possible natural language prompts and the function each will trigger:

| Natural Language Prompt                 | Function                        | Action                                         |
|-----------------------------------------|---------------------------------|------------------------------------------------|
| "Create a new file for Project X"       | `CreateFileInProjectFunction`   | This would initiate a new file creation in the specified project. |
| "Run this code snippet with X args"     | `ExecuteCodeFunction`           | Code execution with provided arguments would be triggered. |
| "Look at my XXXX class"                 | `FindCodeFunction`              | Searches for the specified class named `XXXX` in the codebase. |
| "Find my function named YYYYY"          | `FindCodeFunction`              | Locates the `YYYYY` function within the codebase. |
| "Get the latest errors"                 | `GetErrorsFromVisualStudioFunction` | Retrieves the most recent errors from Visual Studio's error list. |
| "What's the last exception?"            | `GetLastExceptionFunction`      | Captures the details of the last thrown exception. |
| "Show recent debug output"              | `GetRecentMessagesFromAllOutputPanesFunction` | Fetches recent messages from the Debug output window. |
| "Replace ZZZZ with AAAA everywhere"     | `ReplaceCodeFunction`           | Replaces all instances of `ZZZZ` in the codebase with `AAAA`. |
| "I need a new console app named BBBB"   | `CreateProjectInSolutionFunction` | Requests the creation of a new ConsoleApp project with the name `BBBB`. |

#### Example Usage Scenarios

Here are a couple of scenarios exemplifying how you could use natural language prompts to interact with CodexAstra functions:

1. **File Creation**
   - User Prompt: "Create a new file for the MathLibrary project."
   - Action: The `CreateFileInProjectFunction` would be invoked to create a file in the specified "MathLibrary" project.

2. **Code Search**
   - User Prompt: "Look at my MathOperations class."
   - Action: The `FindCodeFunction` would be used to find and display the source code for the "MathOperations" class.

3. **Retrieving Errors**
   - User Prompt: "Show me the errors from my last build."
   - Action: The `GetErrorsFromVisualStudioFunction` would be executed to return the error list from the most recent build performed.

4. **Code Replacement**
   - User Prompt: "Replace 'int' with 'long' in all my variable declarations."
   - Action: The `ReplaceCodeFunction` would be activated to replace instances of 'int' with 'long' across all variable declarations in the current solution.

#### Best Practice for Command Phrasing

When phrasing commands, be clear and precise. The system is designed to understand and respond to key terms and contexts that relate to the functions provided. Unclear or ambiguous prompts may result in unwanted actions or the need for further clarification.

To optimize your interaction, ensure that your prompts:
- Include the name or type of the entity (file, project, class, function, etc.) you are referring to.
- Specify any additional context where possible (e.g., project name, class name, variable types).
- Avoid using vague terms or incomplete sentences that lack actionable information.

By following these guidelines, you can streamline your work process and effectively leverage the capabilities of the CodexAstra functions.

ReflectAndInvokeFunction Usage

The `ReflectAndInvokeFunction` enables the dynamic execution of methods within the Visual Studio environment through reflection. It allows for flexible interaction with the Visual Studio automation APIs by calling methods without the need for direct function prompts.

Triggering ReflectAndInvokeFunction

To utilize the `ReflectAndInvokeFunction`, you would phrase your prompt to reflect an intention to perform an action using reflection. Here are examples of natural language that would lead to the use of this function:

Natural Language Prompt | Function | Action
---|---|---
"Can you execute the GetCurrentSelection method?" | `ReflectAndInvokeFunction` | Calls the `GetCurrentSelection` method from the `VisualStudioEnvironmentHelper` class using reflection.
"Could you please run the SaveAll command in Visual Studio?" | `ReflectAndInvokeFunction` | Executes the `SaveAllAsync` method ensuring all files are saved within the current Visual Studio session.
"I need to fetch the structure of the current solution." | `ReflectAndInvokeFunction` | Invokes the `GetSolutionStructureAsync` method to obtain a summary of the current solution's architecture.

Example Usage Scenario

Dynamic Method Invocation
User Prompt: "Can you save all open documents in the current session?"
Action: `ReflectAndInvokeFunction` would be chosen to call the `SaveAllAsync` method, saving any open documents in Visual Studio.

Tips for Using ReflectAndInvokeFunction

- Method Name: Specify the method name exactly as it appears within the `VisualStudioEnvironmentHelper` or the relevant namespace when prompting for the function.
- Availability: Confirm the method you wish to call is available in the VisualStudioEnvironmentHelper toolkit, and that it can be accessed through reflection.
- Parameters: If the target method requires parameters, state them clearly. For example: "Please invoke the OpenDocumentAsync method with the file path parameter set to 'C:\\MyProject\\Program.cs'."
- Return Type: Consider how you'll handle the method's return type, as some methods may return asynchronous `Task` objects that require awaiting, while others might provide immediate results.

The `ReflectAndInvokeFunction` is a flexible tool for automating a variety of tasks within Visual Studio, assuming familiarity with the methods' signatures and return types.
