---
title: "Join the Journey of Iris: Building a Multilingual Voice Assistant with OpenAI and Picovoice"
date: "2023-07-03T19:43:00+09:00"
description: Dive into the creation of Iris, a multilingual voice assistant that combines OpenAI's GPT models and Picovoice's Porcupine for keyword detection. Discover how you can contribute to this unique blend of advanced AI capabilities and user-friendly interaction.
---

# Introduction

Welcome to the journey of creating your own voice-activated AI assistant. This blog post will guide you through the process of setting up and customizing [Iris](https://github.com/your-github-account/iris), a simple yet powerful voice assistant built using Python and a few powerful libraries and APIs.

![A man is relaxing on a couch, speaking to an AI voice assistant integrated into his smart home system.](./Picture_a_cozy_home_environment_in_the_evening._A_bcdb51fd-cf55-4007-a2b6-46b350eb8e4f.png)

Iris is named after the Greek goddess of the rainbow and messenger of the gods. Just like Iris from the mythology, our Iris is also a messenger. It listens to your voice commands, processes them, and delivers the appropriate response. The name "Iris" is pronounced in Spanish, and you can listen to the correct pronunciation [here](https://github.com/ywkim/iris/blob/main/iris.mp3).

What sets Iris apart from other voice assistants is its ability to understand and respond in multiple languages, its use of the latest AI models for understanding and generating human-like responses, and its open-source nature that invites contributions from developers around the world.

The beauty of Iris lies in its simplicity and customizability. It uses [Picovoice's Porcupine](https://picovoice.ai/products/porcupine/) for wake word detection, [OpenAI's GPT](https://openai.com/research/) models for generating responses, and [pyttsx4](https://github.com/Jiangshan00001/pyttsx4) for text-to-speech conversion. Each of these components can be customized to suit your needs, making Iris a great starting point for anyone interested in building their own voice assistant.

In this blog post, we will delve into the details of the Iris project, explore the technologies it uses, and provide a practical guide on how to use and contribute to Iris. Whether you're a developer looking to build your own voice assistant, a tech enthusiast curious about the latest in voice assistant technology, or someone interested in contributing to an open-source project, this blog post has something for you.

We hope that this blog post will not only provide you with valuable insights into the Iris project but also inspire you to explore the fascinating world of voice assistant technology and AI. Let's get started!

# Getting Started with Iris

## Understanding Iris

Iris is a voice-activated AI assistant that listens for a wake word, transcribes subsequent speech into text, generates a response using OpenAI's GPT model, and speaks the response back to the user. It's a fully voice-operated system, meaning you don't need to type anything to interact with Iris. It's designed to be simple, efficient, and customizable, making it a great starting point for anyone interested in building their own voice assistant.

## Setting Up Iris

Setting up Iris is straightforward. You'll need [Python 3.8](https://www.python.org/downloads/) or higher and the [Poetry package manager](https://python-poetry.org/docs/#installation). Once you have these prerequisites, you can clone the [Iris repository](https://github.com/ywkim/iris) from GitHub and install the necessary dependencies with Poetry.

After that, you'll need to obtain an [OpenAI API key](https://beta.openai.com/signup/) for the GPT model and a [Picovoice AccessKey](https://picovoice.ai/console/) for the wake word detection. These keys should be placed in a `config.ini` file in the root directory of the project.

Finally, you can run Iris using the command `poetry run python main.py`. Iris will start listening for the wake word and respond to your commands.

## Customizing Iris

One of the great features of Iris is its customizability. You can change the wake word from the default "jarvis" to anything you want by using a [custom wake word model](https://picovoice.ai/console/) from Picovoice. You can also change the voice of Iris's responses by modifying the `voice` setting in the `config.ini` file.

## Expanding Iris

While Iris is a fully functional voice assistant as it is, there's always room for improvement and expansion. You could add more features, like the ability to control smart home devices, set reminders, or even tell jokes. The possibilities are only limited by your imagination and coding skills. If you come up with a great idea or improvement, don't hesitate to [contribute to the project](https://github.com/ywkim/iris) on GitHub.

Remember, Iris is just the beginning. It's a foundation upon which you can build your own unique voice assistant. So get started, experiment, and most importantly, have fun!

# Deep Dive into Iris's Technology Stack

In this section, we'll take a closer look at the technologies that power Iris. We'll start with how Iris listens for its wake word to start processing commands, then we'll move on to how it detects when you're speaking and transcribes your speech into text. Let's dive in!

## Wake Word Detection with Porcupine

The first step in interacting with Iris is to get its attention, and we do this with a "wake word". A wake word is a special phrase that the system is always listening for, which tells it to wake up and start processing further speech as commands or queries. In our case, we're using a default wake word of "Jarvis".

To implement wake word detection, we're using the [Porcupine](https://picovoice.ai/products/porcupine/) library. Porcupine is a highly-accurate and lightweight wake word detection library that works on-device, meaning it doesn't need to send any data to the cloud. This is great for privacy and efficiency.

One of the cool features of Porcupine is that it allows you to define your own custom wake words. This means you can personalize Iris to respond to a different name if you want! To do this, you'll need to use the [Picovoice Console](https://console.picovoice.ai/) to create and train a model for your custom wake word, and then replace the default model file in the Iris configuration with your new one. This is a powerful feature that allows you to customize Iris without having to modify the code.

## Voice Activity Detection and Transcription

Once Iris has been activated with the wake word, it needs to listen to what you say and convert that speech into text that it can process. This involves two steps: Voice Activity Detection (VAD) and transcription.

VAD is the process of identifying when speech is happening. It's used to make sure Iris doesn't waste time and resources processing silence or background noise. For VAD, we're using the [SpeechRecognition](https://pypi.org/project/SpeechRecognition/) library's built-in functionality.

After VAD, the next step is transcription, which is converting the detected speech into written text. For this, we're using OpenAI's Whisper ASR API. Whisper is an Automatic Speech Recognition (ASR) system that has been trained on a large amount of multilingual and multitask supervised data collected from the web. It's designed to convert spoken language into written text and works great for our purposes. You can learn more about it [here](https://openai.com/research/whisper/).

## Conversational AI with GPT

Once Iris has transcribed your speech into text, it needs to understand what you're asking and generate a meaningful response. For this, we're using OpenAI's GPT model.

GPT, or Generative Pretrained Transformer, is a type of language processing AI model that's great at understanding and generating human-like text. It's been trained on a diverse range of internet text and can generate creative, coherent, and contextually relevant sentences. You can learn more about GPT [here](https://openai.com/research/gpt/).

In our case, we're using the GPT model to power Iris's conversational abilities. When you ask Iris a question or give it a command, the text of your request is sent to the GPT model, which generates a response. This response is then spoken out loud by Iris, giving you the information or confirmation you asked for.

## Text-to-Speech with pyttsx4

The final step in the Iris interaction process is speaking the generated response back to you. For this, we're using a text-to-speech (TTS) library called [pyttsx4](https://github.com/Jiangshan00001/pyttsx4).

pyttsx4 is a TTS library for Python that works offline and is compatible with both Python 2 and 3. It supports multiple TTS engines, including native ones on Windows, Mac, and Linux, and it can use any TTS voice installed on your system.

In our Iris configuration, we've set up pyttsx4 to use a specific voice, but you can change this to any voice you like. You can even install additional voices and use them with pyttsx4, allowing you to further customize how Iris sounds.

And that's it! That's the technology stack that powers Iris.

## Bringing It All Together

Now that we've gone through each component of Iris's technology stack, let's take a step back and look at how it all fits together.

When you say the wake word, Iris starts recording your voice. This recording is then transcribed into text using Whisper ASR. The transcribed text is sent to the GPT model, which generates a response. This response is then converted into speech using pyttsx4 and spoken out loud by Iris.

This entire process happens in real-time and is completely hands-free, making Iris a truly voice-activated AI assistant. And the best part? All of this is customizable. You can change the wake word, the language, the voice of Iris, and even the AI model used for conversation.

This level of customization makes Iris a versatile tool that can be adapted to a wide range of use cases. Whether you want a personal assistant to help you manage your schedule, a voice-activated controller for your smart home devices, or a conversational AI for your business, Iris can be tailored to meet your needs.

And because Iris is open-source, you can dive into the code, understand how it works, and even contribute to its development. We believe in the power of community and collaboration, and we're excited to see what you can do with Iris.

## Building Your Own Voice Assistant with Iris

Building your own voice assistant with Iris is as simple as cloning the [repository](https://github.com/ywkim/iris) and setting up your configuration file. But the real power of Iris comes from its customizability. You can change the wake word, the language, the voice of Iris, and even the AI model used for conversation. This means you can tailor Iris to suit your specific needs and preferences.

For example, if you're a business owner, you might want to use Iris as a voice-activated customer service assistant. You can customize the wake word to be your business name, and set up the AI model to respond to customer inquiries. Or if you're a developer, you can use Iris as a hands-free coding assistant, setting up the AI model to understand and respond to coding-related commands.

The possibilities are endless, and we're excited to see what you can create with Iris.

## Contributing to Iris

We believe in the power of community and collaboration, and we're excited to welcome contributors to Iris. Whether you're a developer looking to add new features, a designer wanting to improve the user interface, or a user who's found a bug, your contributions are valuable and appreciated.

To contribute to Iris, you can start by exploring the [code](https://github.com/ywkim/iris) and understanding how it works. If you have an idea for a new feature or improvement, feel free to open an issue on the GitHub repository to discuss it. We're always open to new ideas and feedback.

We also encourage you to join our [Discord community](https://discord.gg/yourdiscordlink), where you can connect with other Iris users and contributors, share your ideas, and get help with any issues you might encounter.

By contributing to Iris, you're not only helping to improve the project, but also becoming part of a community of people passionate about voice technology and AI. We can't wait to see what you'll bring to Iris.

## Real-world Applications of Voice Assistants

Voice assistants are becoming increasingly prevalent in our daily lives. From smart home devices to in-car systems, they provide a hands-free and intuitive way to interact with technology. Here are a few examples of how voice assistants like Iris are being used in the real world:

- **Smart Home Automation:** Voice assistants can control smart home devices, such as lights, thermostats, and security systems. For example, you can ask Iris to turn off the lights in your living room or adjust the temperature in your home.

- **Personal Assistance:** Voice assistants can help with tasks like setting reminders, making appointments, sending messages, and more. You can ask Iris to remind you of an upcoming meeting or send a message to a colleague.

- **Accessibility:** For individuals with physical disabilities or mobility issues, voice assistants can provide a valuable tool for accessing technology and information.

- **Education:** In educational settings, voice assistants can be used to answer questions, provide explanations, and assist with learning. Iris, with its ability to use OpenAI's powerful GPT models, can be a helpful study companion.

## Conclusion

Building a voice assistant like Iris is a fascinating journey into the world of voice technology and AI. It's a project that combines several different technologies to create a system that can understand and respond to voice commands. While Iris is a simple voice assistant, it demonstrates the potential of voice technology and how it can be customized and extended.

Whether you're a developer looking to explore voice technology, a business owner considering a voice assistant for customer service, or a tech enthusiast curious about AI, we hope this blog post has provided you with valuable insights and inspired you to start your own journey with voice assistants.

## References

- [Picovoice](https://picovoice.ai/)
- [OpenAI](https://openai.com/)
- [pyttsx4](https://github.com/Jiangshan00001/pyttsx4)
- [SpeechRecognition](https://pypi.org/project/SpeechRecognition/)
