# My SOP
### I want to join the AI community because I am really interested in this field and want to be a part of community where we enjoy and build crazy stuff. My short term goal is to learn from the SOS and SOC project on Gen AI and AI agents. In the long run, I want to crack a well paying tech job or maybe start my own thing.i wish to pitch and sell AI automations to local businesses in the upcoming months.
### My motivation for AIC started when I came across the INSTIGPT repo looking at all that code and data scrapping scripts, It really inspired me and I wanted to make something like that myself. I’m looking for a community where I can find like minded people, win hackathons, enjoy and build cool stuff together.

### Talking about my background, I come from chemical engineering. I did WIDS in NLP and I was also a trainee in racing team where I learnt about computer vision and YOLO. I also trained MLP and CNN models on MNIST dataset. Right now, I am doing SOS in Gen AI and SOC in building AI agents. Just after doing this assignment I already learnt lot of things like LLM API integration, RAG, transfer learning, transformers etc.

### I will contribute to the community by using what I already know and also learning new tools and concepts. I like building projects that actually solve problems. I will also take part in hackathons. I have good design skills and I can do okayish video editing which I think can help in making sessions and hackathon events better in future.

### I also want to help make the AI community more visible in insti. Like conduct offline hackathons, maybe colab with other clubs and organise sessions so more people get started on building ai and building with ai. (sessions such as  ai automations using n8n ; colabs with clubs like erc to conduct workshops on building talking robots or some cool thing)

### I want to learn alot, make some awesome friends, win hackathons and boast on linkedin and most importantly enjoy doing all this.

# BONUS PART : project ideas

##  24/7 WhatsApp AI Agent for IITB:

### PS and Real World Impact

Students face frequent challenges when trying to find info about administrative offices, emergency services, course related queries, deadlines, and other institutional services. Queries such as how do i get in touch with mental welness program or What time does the biometric office open? or what are the exam weightage for MA110? Where do i see my mess bil? etc

To solve this, I propose a **24/7 WhatsApp-based AI Help Agent**, developed in collaboration with the institute. It can answer queries about office timings, contact details of departments and emergency teams (QRT, hospital, etc.), course registration, timetable lookups. This ensures that students always have instant access to info in a familiar messaging platform, even during non office hours.

## Technical Approach and Feasibility

- **Platform**: WhatsApp Business API using Twilio , easy with n8n integration.
- **Backend**: python based server with webhooks or n8n workslow nodes.
- **Model**: Retrieval Augmented Generation (RAG) using LLMs like OpenAI , Deepseek etc.
- **Knowledge Base**: Structured data scraped from institute websites, PDFs, notices, academic calendars, and announcements stored in a vector db like pinecone , faiss , chromadb.
- **Response Format**: Sends back relevant links, images, or documents .

Feasibility is high, given the maturity of the WhatsApp API ecosystem and availability of LLM services and infrastructure.

## Roadmap: Concept to Prototype

### Collect Data and finalise tech stack   --->   design overall architecture   --->   clean and store scraped data in vector db   --->   BUild Agents to accurataly generate a reply   --->   Build whatsapp chatbot integrated with backedn APIs    --->   connect LLMs with vector db and with whatsapp backend   --->   Deployment and testing.
