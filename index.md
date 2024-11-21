# Caldera

### **Team Members**
Andrew Moore, Jack Guo, Max Villarreal-Blozis, Nick Eastham

---

## **Executive Summary**

### **The Project**
This project aims to deliver a novel, privacy-protecting wearable AI system by utilizing a hybrid approach of local and cloud models.

### **The Problem**
Current AI wearable devices compromise user privacy for simplicity by offloading all processing to cloud models. This exposes sensitive data, increases latency, and leads to subpar performance in many use cases. Additionally, these products fail to optimize the use of different models for specific tasks:
- **GPT-4o** has superior question-answering capabilities but lacks advanced vision features.
- **Google Cloud Vision** outperforms other tools for image-based tasks but is not ideal for natural language processing.

### **Our Solution**
Using a **hybrid local/cloud approach**, our system:
- **Processes simple queries locally** for quicker response times and reduced bandwidth usage.
- **Sends complex queries to the cloud** to ensure higher-quality responses.
- **Incorporates a private relay system** to obfuscate user activity, ensuring privacy while interacting with cloud providers.

---

## **Related Work**
This system draws inspiration from privacy and security-focused technologies, including:
- [Cloudflare Tunnel and Warp](https://www.cloudflare.com)
- Apple’s [On-Device/Private Cloud Compute](https://security.apple.com/blog/private-cloud-compute/)
- [iCloud Private Relay](https://www.apple.com/icloud/docs/iCloud_Private_Relay_Overview_Dec2021.pdf)

The architecture improves upon existing products such as the Rabbit R1, Humane AI Pin, and Brilliant Labs’ Noa by prioritizing **privacy**, **speed**, and **user experience**.

---

## **The Proposal**
Our wearable AI system prioritizes **privacy**, **speed**, and **response quality**. Below are the system's core goals:

### **Goals**
1. **Create a Wearable Device**
   - **Hardware**: Use Brilliant Frame glasses for their robust hardware capabilities and ease of integration.
   - **Software**: Leverage on-device processing for local query handling.

2. **Implement Local Processing**
   - **Hardware**: A Raspberry Pi (or equivalent mobile device).
   - **Software**:
     - Use [Ollama](https://ollama.ai) for simple Llama model queries.
     - Build systems to process vision/audio data and display results on the wearable.

3. **Build a Private Relay System**
   - **Hardware**: Low-cost VPS or university-provided infrastructure.
   - **Software**: Flask-based HTTP relay to anonymize user data before sending queries to cloud APIs.

4. **Design an Intuitive User Interface**
   - **Hardware**: Depends on the wearable device.
   - **Software**:
     - Use Python and Lua for the Brilliant Frame SDK.
     - Explore options for low-cognitive-load user interactions.

---

## **Requirements**

### **Hardware**
- Raspberry Pi 5 (8GB RAM): $80
- Brilliant Frame Glasses (provided by sponsor): $349
- Cloud Hosting (AWS, GCP, DigitalOcean, or university infrastructure).

### **Software**
- **Local Processing**:
  - OpenAI Whisper for voice recognition.
  - OpenAI GPT-4o Mini for conversational tasks.
  - OpenAI TTS for text-to-speech (or a lower-quality local alternative).
- **Cloud Processing**:
  - Google Cloud Vision for image recognition tasks.
  - Google Natural Language for up-to-date world knowledge queries.

---

## **Architecture**

### **System Workflow**
1. **Human Interface Device (HID)**: 
   - Collects user input (voice, vision, or text) and sends data to the Raspberry Pi.
2. **Local Processing**:
   - A fine-tuned DistilBERT model determines whether a query can be processed locally.
   - Simple queries are processed using on-device Llama or GPT-Neo models.
3. **Private Relay System**:
   - Routes complex queries to cloud APIs (e.g., OpenAI GPT-4o, Google Cloud Vision) while anonymizing user data.
4. **Cloud Processing**:
   - Processes the request and sends results back through the private relay to the Raspberry Pi, which displays the output on the wearable device.

---

## **Tech Stack**

- **Wearable Device**: Brilliant Frame Glasses
- **Local Processing**: Raspberry Pi 5, Llama API, Ollama, Whisper
- **Private Relay**: Flask, AWS/GCP/DigitalOcean VPS
- **Cloud Models**: OpenAI GPT-4o, Google Cloud Vision, GNL
- **Programming Languages**: Python, Lua
- **Frameworks**: Flask, Hugging Face (DistilBERT)

---

## **Design Details**

1. **Privacy First**:
   - The private relay removes user-identifiable information from requests before they are sent to cloud APIs.
   - All on-device processing uses open-source or proprietary tools to minimize data exposure.

2. **Hybrid Processing**:
   - Locally handle simple tasks like arithmetic and basic queries for reduced latency.
   - Route complex tasks requiring advanced reasoning or vision to cloud providers.

3. **Modular and Extensible**:
   - Allows enthusiasts to customize the system with additional models or APIs (e.g., Shazam for music recognition).

---

## **References**
- [Cloudflare Tunnel and Warp](https://www.cloudflare.com)
- [Apple Private Cloud Compute](https://security.apple.com/blog/private-cloud-compute/)
- [Brilliant Frame SDK](https://docs.brilliant.xyz/frame/building-apps-sdk/)
- [Google Cloud Vision API](https://cloud.google.com/vision/overview/docs/)
- [OpenAI Whisper API](https://platform.openai.com/docs/models/whisper)

---
