---
title: "Blog 1"
date: 2025-09-10
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

## Building a Speech Intelligence System with AssemblyAI's Speech-to-Text Model from AWS Marketplace

Author: Shun Mao and Zackary Klebanoff

Published: April 16, 2025

Source: AWS Marketplace Blog

# Introduction

Speech intelligence technology and Speech-to-Text (STT) have become essential as organizations collect thousands of hours of call recordings, meetings, and customer interactions each day. However, raw audio data alone cannot provide actionable insights — organizations need the capability to leverage intelligence to extract value from speech data at scale.

Speech intelligence combines speech recognition technology, natural language processing (NLP), and machine learning (ML) to convert audio data into actionable insights. Modern STT models are capable of transcribing conversations with high accuracy and work in tandem with other auxiliary tools to analyze sentiment, detect main topics, and create automatic summaries to provide deeper insights.

Speech intelligence and STT technologies are widely applied in various industries, such as call analytics, conversational intelligence, medical transcription, customer service, video content optimization, legal compliance, sales training and analysis, and more. With the rise of generative AI and increasingly advanced models, the demand for efficient STT models continues to grow in these applications.

---

## About AssemblyAI

AssemblyAI, an Independent Software Vendor (ISV) on AWS Marketplace, is a research-driven organization focused on advancing and democratizing speech AI technology globally. Founded in 2017, the company has built a team of interdisciplinary researchers, scientists, and engineers working towards developing state-of-the-art speech AI models, unlocking new possibilities for audio-based applications.

AssemblyAI's technology serves thousands of customers and hundreds of thousands of developers worldwide through a simple, developer-friendly API. AssemblyAI provides comprehensive speech AI capabilities, including:

- Core Speech-to-Text

- Speaker Detection

- Automatic Language Detection

- Sentiment Analysis

- Chapter Detection

- PII (Personally Identifiable Information) Redaction

AssemblyAI's Universal-2 model demonstrates the company's commitment to pushing the limits of speech AI technology. This model achieves high accuracy by addressing key challenges in speech recognition, improving the recognition of proper nouns, text formatting, capitalization, and accurate timestamp creation. AssemblyAI takes a research-based approach to building robust and easily integrable speech AI models.

This article will guide you on how to get started with AssemblyAI's API on AWS Marketplace, while also building an initial Proof of Concept (POC) by making API calls in just a few simple steps.

---


## Solution Overview

AssemblyAI's Speech-to-Text service processes audio through a two-stage pipeline.
In the first stage, the system uses the Universal-2 ASR (Automatic Speech Recognition) model — a Conformer RNN-T model with 600 million parameters, trained on 12.5 million hours of multilingual audio data. This model can transcribe speech to text while effectively handling complex situations, such as multiple speakers, regional accents, and background noise.
In the second stage, the system applies neural models to format the text, adding punctuation, capitalization, and text normalization to produce a clean, readable, and professional transcript.

In addition to core transcription, users can activate additional AI models that run in parallel with the main ASR process. These models include:

- Speaker Identification – determining who is speaking in a conversation.

- Sentiment Analysis – understanding the tone and sentiment in speech.

- Topic Detection – automatically classifying the conversation's content.

- Content Summarization – extracting key points and summaries.

- PII Redaction – ensuring compliance with privacy requirements.

All these models seamlessly integrate through the same API interface, making it easy for developers to incorporate and expand speech analytics capabilities.

<img src="/images/blog1.png" alt="High-level Architecture Diagram for AssemblyAI's Transcription API" width="600">

> *Figure 1: High-level Architecture Diagram for AssemblyAI's Transcription API*

---

## Prerequisites

Before you begin, ensure you have the following:

- An Amazon Web Services (AWS) account with access to Amazon Simple Storage Service (Amazon S3).

- AssemblyAI's API service is available for purchase on AWS Marketplace. You can also sign up for a trial account directly on AssemblyAI’s website.

- Once you've created your AssemblyAI account, store your API key securely for use in the next steps.

Next, run the following Python code to prepare for the implementation scenarios in the solution walkthrough:

    !pip install assemblyai

    import assemblyai as aai

    aai.settings.api_key = "xxxxxxxx"  # Your AssemblyAI API key


---

## Solution Walkthrough

In this section, we will explore five use cases where AssemblyAI's API can deliver significant value. Each case is accompanied by a code snippet, enabling readers to experiment within their own environment.

  1. Transcribing Audio from a Local File

  2. Transcribing an Audio File from Amazon S3

  3. Speaker Diarization

  4. Automatic Language Detection

  5. PII Redaction

---

## Transcribing Audio from Amazon S3

In many organizations, audio data is stored in cloud storage services like Amazon S3. To transcribe an audio file from an S3 bucket, AssemblyAI requires temporary access to that file.

To grant this access, you need to create a pre-signed URL, which is a special link that provides access to the file for a limited time.

For more details on how to create a pre-signed URL, refer to the AWS documentation: “Sharing Objects with Pre-signed URLs.”

Execute the following Python code to perform transcription:

    import requests
    import time

    p_url = "S3 pre-signed url"

    assembly_key = "xxxxxxxx"  # Your AssemblyAI API key

    # Use the API key for authentication
    headers = {"authorization": assembly_key, "content-type": "application/json"}

    # AssemblyAI's transcription API endpoint
    upload_endpoint = "https://api.assemblyai.com/v2/transcript"

    # Use the pre-signed URL for the audio file in the POST request
    json = {"audio_url": p_url}

    # POST request to queue the audio file for transcription
    post_response = requests.post(upload_endpoint, json=json, headers=headers)

    # Get the processing endpoint
    get_endpoint = upload_endpoint + "/" + post_response.json()["id"]

    # GET request to check the transcription status
    get_response = requests.get(get_endpoint, headers=headers)

    # If transcription is not yet complete, wait until it's finished
    while get_response.json()["status"] != "completed":
        get_response = requests.get(get_endpoint, headers=headers)
        time.sleep(5)

    # When transcription is complete, print the result
    print(get_response.json()["text"])


---

## Transcribing Audio from a Local File

This is a simple setup where audio files are stored in the local directory where the code is executed.

AssemblyAI's API supports most popular audio and video formats like mp3, m4a, m4p, wav, or wma.

For optimal recognition quality, it's recommended to use the raw format of the audio file rather than converting it to another format.

For more details about supported audio file formats, refer to AssemblyAI’s blog.

Download a publicly available audio file from AssemblyAI's website, and save it to your local directory.

Execute the following code to transcribe the file:

    # Transcribe a local audio file
    transcriber = aai.Transcriber()
    transcript = transcriber.transcribe("./Audios/ford_clip_trimmed.mp3")

    print(transcript.text)


---

## Speaker Diarization

Speaker diarization is an important part of audio processing, as it addresses the challenge of identifying who speaks and when in a recording. This capability is essential for many tasks, such as improving clarity and structure, supporting advanced analytics, and enabling content personalization.

Execute the following code to perform transcription:

    config = aai.TranscriptionConfig(speaker_labels=True)
    transcriber = aai.Transcriber(config=config)

    FILE_URL = "https://github.com/AssemblyAI-Examples/audio-examples/raw/main/20230607_me_canadian_wildfires.mp3"

    transcript = transcriber.transcribe(FILE_URL)

    # Extract all the speech utterances from the response
    utterances = transcript.utterances

    # For each utterance, print the speaker and their speech
    for utterance in utterances:
        speaker = utterance.speaker
        text = utterance.text
        print(f"Speaker {speaker}: {text}")

---
## Automatic Language Detection
Automatic language detection is another key feature in audio analysis, as it helps the system process and understand spoken content more accurately and effectively.

This feature enhances the user experience in multilingual applications and allows for customization based on specific languages.

Execute the following code to perform transcription:

    config = aai.TranscriptionConfig(language_detection=True)
    transcriber = aai.Transcriber(config=config)

    FILE_URL = "https://assembly.ai/news.mp4"

    transcript = transcriber.transcribe(FILE_URL)

    print(transcript.json_response['language_code'])

---
## PII Redaction
Security is a top priority at AWS and AssemblyAI.

The PII redaction feature provided by AssemblyAI helps maintain privacy and security for sensitive information, allowing customers to build secure and compliant applications without legal or regulatory risks.

Users can control which types of sensitive data (e.g., credit card numbers, email addresses, phone numbers) to redact through configuration, as demonstrated in the following code snippet:

    config = aai.TranscriptionConfig()

    config.set_redact_pii( 
      policies=[
          aai.PIIRedactionPolicy.credit_card_number,
          aai.PIIRedactionPolicy.email_address,
          aai.PIIRedactionPolicy.location,
          aai.PIIRedactionPolicy.person_name,
          aai.PIIRedactionPolicy.phone_number,
      ], 
      substitution=aai.PIISubstitutionPolicy.hash, 
    )

    transcriber = aai.Transcriber(config=config)

    FILE_URL = "https://example.org/audio.mp3" 

    transcript = transcriber.transcribe(FILE_URL)

    print(transcript.text)
---
## Conclusion
AssemblyAI is committed to building a high-quality API platform for developers to convert and understand speech data using AI, enabling the creation of innovative products and services.

AssemblyAI's speech-to-text models address critical challenges in the transcription process, and their latest model — Universal-2 — focuses on solving "edge-case" issues that impact real-world speech AI, such as improving accuracy for numbers, special characters, and rare words.

Learn more about the improvements in Universal-2: [Read AssemblyAI's Blog]
See how AssemblyAI compares to competitors: [View Performance Comparison Chart]
Explore the research behind Universal-2: [Learn More About Research]

You can start using AssemblyAI's API by visiting the product page on AWS Marketplace or by creating an account directly on AssemblyAI's website.

---
## About the Authors

Shun Mao

        Shun Mao is a Senior Partner Solution Architect in the Independent Software Vendor (ISV) partner group, specializing in Artificial Intelligence and Machine Learning (AI/ML) at Amazon Web Services (AWS). He has many years of experience in data science, analytics, AI, and cloud computing across various industries, including oil and gas and pharmaceuticals. At AWS, he supports strategic AI/ML partners in developing creative products and solutions that deliver business value to customers. Outside of work, Shun enjoys fishing, traveling, and playing table tennis.

Zackary Klebanoff

        Zackary Klebanoff is a Senior Solution Architect at AssemblyAI. He has several years of experience helping customers leverage speech AI technology to build exceptional products and applications. Throughout his career, he has worked at startups, helping them grow by bridging the gap between technology and practical applications. Outside of work, Zackary enjoys playing basketball, attending concerts, and supporting the Philadelphia Eagles football team.

---