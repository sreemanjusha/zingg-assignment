Overview :
The Labeller.java class is responsible reading data , preprocessing data , post processing data , user interaction CLI and updating training data. Functionally the overall
class is correct but it has significant issues around testability, separations of concerns and extensibility.

Key Issues:
1. Tight Coupling and Low Maintainability : The class handles multiple responsilities and actions like accessing the data , business logic , state management and logging and User Interaction (CLI)
2. Tight coupling with CLI : The use of Scanner(System.in) and hardcoded input logic ties the implementation strictly to CLI which cannot extend to UI and APIs
3. Poor dependency management : methods can be injected instead of instantiating internally and leading to complexity and poor readability
4. Poor error handling : Usage of exception and silent fallbacks
5. Usage of harded coded values : values like [0129] and QUIT_LABELING = 9 are harded coded

Remediations:
1. Separating the concerns and breaking them into smaller classes
   a. Labelling
   b. DataService
   c. PreprocessingService
   d. LabellingEngine
   e. UserInteractionHandler
2. Using an interface will enable multiple implementations
3. Using dependency injections will improve testability , decoupling and flexibility
4. Using specific exceptions and meaningful logs wherever required
5. Replacing the hardcoded values with enum

Conclusion :
The current implementation is functional but not scalable. Refactoring this toward a modular , interface driven , dependency injected design will significantly improve its
readability , maintaintability, scalability , and testability. This will also enable support for multiple interactions beyond CLI.
