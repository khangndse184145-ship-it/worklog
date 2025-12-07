---
title: "Blog 2"
date: 2025-09-10
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

## Tapestry Makes Enterprise Knowledge More Accessible with Generative AI on AWS
Authors: Nishant Singh, Aditya Pendyala, Aravind Narasimhan, and Karthigeyan Ramakrishnan

Published: February 26, 2025

Category: Amazon Aurora, Amazon Bedrock, Amazon Bedrock Knowledge Bases, Amazon CloudFront, Amazon S3, AWS IAM, AWS Lambda, Retail

## Introduction

Generative AI has the potential to change the way large companies operate. For businesses, information is often stored in silos across different teams. By combining large language models (LLMs) with powerful knowledge bases, organizations can create intelligent systems that not only store information but also understand it—making enterprise knowledge more accessible and usable than ever before.

Tapestry, a technology company that owns iconic brands like Coach and Kate Spade, is leading the way in applying generative AI to transform their enterprise knowledge management model. By leveraging AWS, the company has developed an intelligent information management system that centralizes data access across business units, helping employees make faster and better decisions.

## Transforming Enterprise Knowledge Management with AI on AWS

Tapestry has nurtured a technology innovation culture in the luxury retail industry, demonstrated by their experimentation and deployment of new solutions. This commitment is evident in their approach to AI: calculated, secure, and aimed at creating business value.

    “We wanted to build an internal generative AI solution before experimenting in the public space,” shared Aravind Narasimhan, Vice President of Applied Technology at Tapestry. “This gives us an opportunity to experiment with the technology, learn, and educate partners within the company.”

Like many large enterprises, Tapestry faced challenges with knowledge management. Information was fragmented across departments such as IT, HR, legal, and others, making it difficult for employees to quickly find answers. Standard operating procedures, policies, and internal knowledge were also stored in different systems and formats. Tapestry saw an opportunity to use generative AI to address this issue.

Amazon Bedrock—providing high-performance foundational models—along with Amazon Bedrock Knowledge Bases, which allows these foundational models and agents to access contextual information from the company’s private data sources—has provided the ideal foundation for building an enterprise-scale solution.

    “Amazon Bedrock Knowledge Bases is a plug-and-play solution with minimal coding requirements,” said Karthigeyan Ramakrishnan, Director of Applications at Tapestry. “You can choose embedding models, vector stores, and LLMs. You can easily configure chunking, tokens, and other parts. That’s why we love it.”

## Building an Enterprise Platform to Share Information Smoothly

The development process lasted 4 months, starting with a proof of concept in the IT department. The knowledge management system uses multiple AWS services. At its core, Amazon Bedrock Knowledge Bases is used to manage and organize the document repository, while Claude 3 Haiku serves as the large language model to handle natural language queries.

To create text embeddings that reflect semantic meaning, Tapestry uses the Titan foundation models in Amazon Bedrock, offering a variety of options for image, multimodal, and text models.

Additionally, Amazon Aurora for PostgreSQL—with high performance and exceptional availability at a global scale—was used as a vector store and index to support fast and efficient semantic search across millions of document segments.

Tapestry’s development team designed the knowledge management system with separate public and private knowledge bases, each configured independently to meet the needs of each department. The public knowledge base is accessible to everyone in the company, containing general operational information, while private knowledge bases are restricted through role-based access control (RBAC) for sensitive department-specific data.

To implement this separation, they used two methods:

  1. Roles in AWS Identity and Access Management (IAM) to manage identity security and access to AWS services and resources.

  2. Integration of the solution with Tapestry’s single sign-on (SSO) system.

The serverless architecture of the solution provides a seamless user experience while ensuring global scalability. Employees can access the knowledge management system from virtually anywhere in the world through the web-based chatbot interface, with content distributed securely by Amazon CloudFront.

When users submit queries, AWS Lambda—running event-driven code and automatically managing computing resources—triggers functions to process the requests, perform necessary security checks, and route queries to the appropriate knowledge base.

Source documents and metadata are stored in Amazon S3—an object storage service that allows large amounts of data to be retrieved from anywhere.

A standout feature of the knowledge management system is its ability to keep content fresh and up-to-date. The Tapestry team has implemented automated processes to scan and update the knowledge bases, ensuring that any changes to the source documents are reflected in the system.

They developed an automated pipeline to monitor the repositories for changes, process new or edited documents using appropriate chunking strategies for each type of content, create new embeddings using Amazon's Titan foundation models, and automatically index those new embeddings in the Aurora PostgreSQL vector store to keep the knowledge base updated.

## Creating Business Value Through Enhanced Knowledge Management

Tapestry is expanding the system’s capabilities to make it an even more powerful solution. Plans include deploying an image search tool to extract and query information from visual content, as well as integrating the solution into other enterprise systems to generate near-real-time reports and data analytics.

    “We’re working to make the system smarter and more interactive with user feedback,” Ramakrishnan shared. “Currently, we have text search, and we’re looking into how we can add voice capabilities. We’re also working on bringing structured data into the system, where users can ask questions about sales, inventory, store traffic, and orders.”

Thanks to generative AI on AWS, Tapestry is breaking down information silos, accelerating decision-making, and preserving valuable organizational knowledge that would otherwise be at risk of being lost. The solution has significantly reduced the time employees spend searching for information and waiting for expertise from within the company. At the same time, these capabilities enable employees to focus on more strategic and innovative work.

    “Our departments benefit from generative AI on AWS because they have to answer fewer routine questions, and from a user perspective, they get what they want faster,” Narasimhan said. “We’ve become more agile and can act faster.”

---
## About the Authors

Nishant Singh

        Nishant is a Senior Customer Solutions Manager (CSM) at AWS, where he focuses his expertise on the retail and consumer packaged goods (CPG) industries. His mission is to help customers design and implement value-based solutions that deliver measurable business outcomes through AWS technologies. With a "customer-first" mindset, he focuses on transforming business challenges into opportunities to drive growth, innovation, and operational efficiency by leveraging the full capabilities of the AWS platform.

Aditya Pendyala

        Aditya is a Principal Solutions Architect at AWS, based in New York (NYC). He has extensive experience in designing cloud-based applications. Currently, he collaborates with large enterprises to help them build scalable, flexible, and resilient cloud architectures, while providing comprehensive cloud solution consulting. Aditya holds a Master’s in Computer Science from Shippensburg University and believes in the saying, "When you stop learning, you stop growing."

Aravind Narasimhan

        Aravind Narasimhan is a seasoned senior leader with a strategic vision for IT, system architecture, technology evaluation, and feasible planning in high-performance environments. Throughout his career, he has led technical implementations for Omni, Cloud, and ERP transformation projects, as well as built and developed Robotic Process Automation (RPA) initiatives. Additionally, Aravind leads the AI Center of Excellence (COE) at Tapestry, where he drives innovation and enhances efficiency in the AI space. Prior to joining Tapestry, he led several initiatives in areas like planning, sales, POS systems, and BI solutions in retail. Aravind holds a degree in Engineering from Bangalore University and an MBA in Finance from Rutgers University.

Karthigeyan Ramakrishnan

        Karthigeyan Ramakrishnan is an experienced IT professional with over 20 years in leadership, architecture, consulting, and implementing innovative IT solutions. He has worked in the retail IT industry, covering various functional areas such as warehouse management, planning, procurement, customer service, automation, and next-generation artificial intelligence (Gen AI). Karthigeyan has global consulting experience across markets in Europe, India, South America, and the US. At Tapestry, he heads Planning and Automation. He has a particular passion for Gen AI and is always looking for ways to harness this technology not just to solve problems, but to explore untapped opportunities. Karthigeyan holds a degree in Chemical Engineering from Anna University, Chennai, and enjoys applying reaction design principles to technology solutions.