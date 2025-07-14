# Functional Requirements 
In this part, we will take a deep dive into **Functional Requirements**, which form the foundation of any system design. Understanding functional requirements is critical because they define what the system **must do** in order to meet the needs of the users. 

In system design interviews, your first task is to ask clarifying questions to gather and confirm the functional requirements. A thorough understanding of the problem space ensures that the system you design meets the expectations and use cases. 

Let's break this part down into actionable steps and learn how to define and handle functional requirements with an example of designing a **URL Shortening Service**.

## What are Functional Requirements?
Functional requirements specify the **core features** and **capabilities** of a system. They describe **what** the system should do, without going into detail about how the system achieves these tasks.

Functional requirements typically include: 
- **User-facing features**: The operations users should be able to perform.
- **System behaviors**: How the system responds to user inputs or requests. 
- **Data flows**: How information is processed, stored, and retrieved within the system. 

## Steps to Identify Functional Requirements

### Understand the Problem Scope 
- Begin by understanding the **problem space** and the goals of the system.
- Ask clarifying questions to understand the core functionality.

Example: For a URL Shortening Service, clarifying questions might include: 
- Should the system allow only authenticated users to shorten URLs, or can anyone use it?
- How long should the short URLs be valid ? Should they expire? 
- Should users be able to customize the short URL? 

### Identify Core Use Cases 
- Identify the main use cases that users will interact with.
- Break down each use case into specific operaitons the system needs to handle. 

#### Example Use Cases for a URL Shortening Service: 
- Shortening a URL: A user provides a long URL, and the system returns a short URL.
- Redirecting: When a user clicks the short URL, the system should redirect them to the original URL.
- Analytics: The system should track the number of clicks on each short URL.
- Manage URLs(optional): If the system supports user accounts, users should be able to view, edit, or delete their previously shortened URLs.

### Prioritize Features 
- Break down the functional requirements into must-have, nice-to-have, and future features. 
- This helps you focus on core functionality and avoid over-designing in an interview. 

Example: For the URL Shortening Service:

#### Must-have Features: 
- Shorten long URLs.
- Redirect users when they access the short URL.
- Store and retrieve the mapping between the short URL and long URL. 

#### Nice-to-Have Features: 
- Provide basic analytics like click tracking.
- Allow users to customize the short URL.

#### Future Features: 
- Add a bulk URL shortening feature for large-scale users. 
- Offer detailed analytics (e.g., geographic data, device type).
- Support user accounts for managing shortened URLs.


