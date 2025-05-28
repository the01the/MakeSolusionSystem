# LLM Consensus Solution Generation System - Zero Cost Architecture

```mermaid
graph TD
    A[User] --> B(Python Script<br>&#40;main.py&#41; on Local PC)
    
    subgraph InputControlLayer
        B -- Input Problem Statement --> C[Problem Requirements]
        B -- Prompt Generation / Discussion Facilitation --> D[LLM Manager / Facilitator]
    end

    subgraph LLMDiscussionEngine_Local_Ollama
        D -- Discussion Instructions / History --> E(Local Ollama Server)
        E -- Model Call --> F(Open Source LLM Models<br>e.g., Llama 3 / Phi-3)
        F -- Opinion / Proposal / Question <--> F
        F -- Opinion / Proposal / Question --> D
    end

    subgraph CodeGenerationExecutionDebugCycle
        D -- Adopted Method / Design --> G[Code Generation Logic<br>&#40;within Python Script&#41;]
        G -- Generated Code<br>&#40;temp_code.py&#41; --> H[Python Subprocess<br>Execution Environment] 
        H -- Execution Result / Log / Error --> I[Debug / Test Logic<br>&#40;within Python Script&#41;]
        I -- Correction Proposal / Test Result --> D
    end

    subgraph DataPersistence_VersionControl
        J[Local File System<br>&#40;Logs / Designs / Code&#41;]
        K[GitHub Private Repository<br>&#40;Code Version Control&#41;]
        D & G & I --> J
        G & H --> K
        J -- History Reference --> D & G & I
        K -- Code History --> G & H & I
    end

    subgraph Communication_Visualization
        L[Discord Bot Interface<br>&#40;within Python Script&#41;]
        M[Discord Channel<br>&#40;LLMs as Bots&#41;]
        D -- Discussion Content / Notification --> L
        L <--> M
    end
