# Mermaid Code Generation FastAPI Server

[Working Demo](https://fab-team.xyz/chat-interface)

[Individual Demos from the team](https://drive.google.com/drive/folders/1-P_toKdJ-SRMLXh0ZMZMdOPXgWeuQkkU?usp=sharing)

## Cloud Infrastructure
![Mermaid Code Generation Miro](https://github.com/user-attachments/assets/57add8df-ce53-43da-ac88-432ae0196e51)

## Web Application
![optillm_webapp](https://github.com/user-attachments/assets/83ae8153-e09a-44d3-be50-b63b07d71eb6)

## Features
- The application uses AWS Bedrock to communicate with Anthropic's Claude 3 Haiku to facilitate a conversation with the user.
- CI/CD pipeline is setup using GitHub Actions to automate deployment on AWS EC2.


## Conversational Bot

This API is used to push user's chat with the bot to the database and returns a 
```json
{
    "userID": "user123",
    "requestID": "request123",
    "user_input": "I want to implement and User registration application for my club",
    "modelParameters": {
        "temperature": 0.75,
        "max_tokens": 2000,
        "top_p": 0.9
    }
}
```
Response:
```json
{
    "user_input": "I want to implement and User registration application for my club",
    "model_output": "What are the main components or features of the user registration application?",
    "wantsToDraw": false
}
```

## Mermaid Code Generation


(would only work if the user has had a chat session before)
This API tells the backend to fetch user chats and return the mermaid code for user requirements.

```json
{
    "userID": "user123",
    "requestID": "request123"
}
```
Response:
```json
{
    "mermaid_code": "\ngraph TB\n\nsubgraph Database\n    style Database fill:#9370DB,stroke:#333,stroke-width:2px\n    DB[PostgreSQL Database]\nend\n\nsubgraph Server\n    style Server fill:#87CEEB,stroke:#333,stroke-width:2px\n    APP[User Registration Application Server]\nend\n\nsubgraph Authentication\n    style Authentication fill:#FFA07A,stroke:#333,stroke-width:2px\n    AUTH[Authentication Service]\n    MFA[Multi-Factor Authentication]\nend\n\nsubgraph User Profile\n    style \"User Profile\" fill:#90EE90,stroke:#333,stroke-width:2px\n    PROFILE[User Profile Management]\nend\n\nsubgraph Registration\n    style Registration fill:#FFD700,stroke:#333,stroke-width:2px\n    REG[Registration Workflow]\n    EMAIL[Email Verification]\n    CONSENT[Consent Management]\nend\n\nsubgraph Security\n    style Security fill:#FF6347,stroke:#333,stroke-width:2px\n    ENCRYPT[Data Encryption]\n    POLICY[Data Protection Policies]\n    COMPLIANCE[Regulatory Compliance]\nend\n\nsubgraph Cloud\n    style Cloud fill:#ADD8E6,stroke:#333,stroke-width:2px\n    AWS[AWS Cloud Services]\nend\n\nDB --> APP\nAPP --> AUTH\nAUTH --> MFA\nAPP --> PROFILE\nREG --> EMAIL\nREG --> CONSENT\nAPP --> ENCRYPT\nAPP --> POLICY\nAPP --> COMPLIANCE\nAPP --> AWS\n",
    "userID": "yash"
}
```

