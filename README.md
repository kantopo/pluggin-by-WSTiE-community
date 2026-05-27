# pluggin-by-WSTiE-community
by students from WSTiE
# Project Overview: Streamlining the Digital Learning Experience
1. Introduction
Our project aims to bridge the gap between complex academic theory and student comprehension. By developing a simplified, accessible learning experience, we provide educational materials authored by students and educators who have personally navigated these challenging subjects. Our primary goal is to ensure that future generations of students can master difficult concepts with greater ease.
During the research phase, we evaluated three primary methodologies for system development:
Custom Development: Building a full-stack solution (Frontend, Backend, and Database) from scratch.
Hybrid Integration: Utilizing an existing LMS backend via API with a custom-designed UI.
LMS Adaptation: Modifying established platforms such as Moodle or edX.
Given the project’s scope, personnel constraints, and timeline, we selected Moodle as our core platform. This allowed us to leverage robust, pre-existing functionality while focusing our resources on content creation for core subjects: Discrete Mathematics, Mathematical Analysis, and Linear Algebra.

2. Project Roles & Responsibilities
Kiryl: Project Manager & Content Author
Michael: Server Administration & Moodle Instance Management
Serhii: Plugin Integration & Content Author
Uliana: Lead Resource Coordinator (PDF Materials)
Illia, Roma, Aleksej, Bohdan, Vitaly: Technical & Content Support Team

3. Server Infrastructure & Deployment
Initial Implementation
To host the development environment, we utilized a private server running Proxmox VE for virtualization. A dedicated Virtual Machine (VM) was provisioned with a standard LAMP stack (Apache, PHP, and MariaDB). We initially deployed Moodle 5.11 (December Stable Release), configured outgoing SMTP for notifications, and optimized PHP limits to accommodate large educational plugins and media files.
Version Alignment & Docker Transition
Following a consultation with Mr. Marcin Kubasiak, we identified a version mismatch between our development environment and the university’s production system. To ensure seamless material migration to the university’s official servers, we pivoted our strategy:
Dockerization: We redeployed the environment using Docker to enhance portability and reproducibility.
Version Parity: The system was downgraded to Moodle 4.5.4 to mirror the university’s environment exactly.
Connectivity
Access was managed via VPN to maintain a secure development perimeter. While we explored public-facing options like Cloudflare Tunnels, we concluded that a VPN provided the most secure environment for internal collaborative development.

4. Plugin Integration & Evaluation
We conducted extensive testing on various plugins to enhance the user experience. Many were discarded due to technical limitations or redundant features:
H5P & PDF Annotation: Dismissed due to editor friction and bugs regarding anonymous permission sets.
Gamification (Level Up XP): Replaced by the more streamlined Completion Progress block.
Multi-Language Content: Found to be manually intensive; we determined that a future AI-driven dynamic translation would be more efficient than static manual entries.
Ultimately, we implemented three essential plugins that provided critical functionality missing from the Moodle core:
MathType (WIRIS): Essential for rendering complex mathematical notation. For optimal performance, we configured the MathType filter at the top of the processing hierarchy.Note: To ensure compatibility with AI-generated LaTeX, we standardized delimiters to \( ... \) instead of $ ... $ to prevent rendering errors.
Completion Progress: Provides students with a visual roadmap of their achievements and remaining tasks.
Mass Actions: Enabled the administrative team to manage content efficiently, performing bulk moves and edits that the standard interface does not support.

5. Course Structure & Pedagogical Design
We organized the platform into a hierarchical structure under the "Rok 1" category, spanning Probability & Statistics, Mathematical Analysis & Linear Algebra, and Discrete Mathematics.
Each topic follows a rigorous pedagogical template:
Simplified Theory: Core concepts explained in plain language, focusing on high-impact information.
Multimedia Integration: Supplemental video lectures for visual learners.
Adaptive Quizzes: Assessments are set to "Adaptive Mode," providing immediate feedback. Incorrect answers offer hints, while correct answers provide full step-by-step solutions to reinforce the logic.
Resource Repository: Curated PDF materials provided by faculty served as the academic foundation for our digitized content.
Collaborative Forums: Discussion boards with mandatory subscriptions and disabled anonymity to foster a professional and accountable peer-learning environment.
