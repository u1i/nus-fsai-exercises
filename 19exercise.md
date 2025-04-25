# Hands-On Exercise: Exploring LLM Behavior with a Playground

**Course:** Full Stack with AI (NUS)   
**Module:** 19 - Generative AI Application

## Introduction

This exercise provides a practical introduction to interacting with Large Language Models (LLMs) using a web-based playground. We will explore how to influence an LLM's behavior through system prompts, control its creativity using temperature settings, and compare the capabilities of different models. This will help solidify concepts discussed in Module 19, such as prompt engineering, LLM parameters, and model selection.

We will use the **AI Chat Playground** ([https://chat.naida.ai/](https://chat.naida.ai/)) which provides a simple interface to Google's Gemini models.

## Prerequisites

*   A modern web browser (like Chrome, Firefox, Edge).
*   A Google Account.
*   An active internet connection.

## Setup: Configuring the AI Chat Playground

1.  **Get Your API Key:**
    *   You need a Google AI API key to use the playground. You can get one for free from Google AI Studio.
    *   Go to: [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
    *   Log in with your Google Account if prompted.
    *   Click on "**Create API key in new project**" (or use an existing project if you have one).
    *   Copy the generated API key. **Keep this key secure and do not share it publicly.**

2.  **Configure the Playground:**
    *   Open the AI Chat Playground in your browser: [https://chat.naida.ai/](https://chat.naida.ai/)
    *   Click the **settings icon** (⚙️) in the top right corner.
    *   Paste your copied Google AI API key into the "**API Key**" field.
    *   Click the "**Test API Key**" button. You should see a confirmation message if the key is valid.
    *   For now, leave the **Model** set to the default (**Gemini 1.5 Flash**) and the **Temperature** at its default (likely around 0.4).
    *   Leave the **System Prompt** field empty for now.
    *   Click outside the settings box to close it.

**Understanding the LLM Landscape:**

The playground lets you select different Google Gemini models. The world of LLMs is vast, with many models available (OpenAI's GPT series, Anthropic's Claude, Meta's Llama, etc., plus many open-source options). Choosing the right model is crucial and depends on factors like:

*   **Capability:** Some models are better at reasoning, creativity, or handling large amounts of text.
*   **Speed:** Smaller models (like Flash) are generally faster than larger ones (like Pro).
*   **Cost:** Using models via API usually incurs costs based on usage (input/output tokens). Free tiers often exist but have limits. Google's models are currently quite affordable with generous free tiers.
*   **Rate Limits:** More powerful models might have stricter usage limits (e.g., only a few requests allowed per minute on free tiers).

Now you are ready to start experimenting!

## Part 1: The Power of the System Prompt

**Key Insight:** The System Prompt sets the context, persona, and rules for the LLM's behavior throughout a conversation. It's a powerful tool for guiding the AI.

1.  **Set the Scene:**
    *   Click the **settings icon** (⚙️).
    *   Set the **Temperature** to `0.7`. (This allows for some creativity and personality).
    *   In the **System Prompt** field, copy and paste the following text exactly:
        ```
        You are Pip, a quirky and slightly sarcastic AI assistant. You love puns and try to keep your answers concise, often ending with a playful sign-off. You avoid overly technical jargon.
        ```
    *   Close the settings.

2.  **Interact with Pip:**
    *   In the chat input box, ask a few different questions. Try things like:
        *   "Explain what a CDN is."
        *   "What's the weather like today?" (It might hallucinate, that's okay!)
        *   "Suggest a name for a pet robot."
    *   Observe the responses. Does the AI adopt the persona of Pip? Notice the tone, conciseness, and maybe even puns or quirky sign-offs.

3.  **Compare without System Prompt:**
    *   Click the "**Start fresh chat**" button (bottom right, looks like a refresh icon). This clears the memory *but keeps your settings*.
    *   Go back into Settings (⚙️) and **delete** the text from the **System Prompt** field, leaving it empty.
    *   Close the settings.
    *   Ask the *same* questions you asked Pip before.
    *   Compare the responses. How are they different without the system prompt defining the persona? The answers will likely be more generic and neutral.

**Explanation:**

The System Prompt acts as a persistent instruction guiding the LLM's responses for the entire chat session. By defining a persona ("Pip, the quirky AI"), rules ("concise answers," "love puns"), and constraints ("avoid jargon"), you fundamentally change how the model interacts. Temperature set to 0.7 gives the model enough "freedom" to express this personality. Without a system prompt, the LLM defaults to a more standard, helpful assistant mode. Feel free to experiment with different system prompts to create other AI personas!

## Part 2: Temperature - Controlling Creativity vs. Determinism

**Key Insight:** The Temperature setting controls the randomness of the LLM's output. Low temperature makes the output more focused and predictable (deterministic), while high temperature makes it more creative and varied (and potentially less coherent).

1.  **Deterministic Output (Low Temperature):**
    *   Click "**Start fresh chat**".
    *   Go into Settings (⚙️).
    *   Ensure the **System Prompt** is empty.
    *   Set **Temperature** to `0.0`.
    *   Close settings.
    *   Ask a simple, factual question: `What is the capital of Singapore?`
    *   Note the exact response.
    *   Click "**Start fresh chat**" again.
    *   Ask the *exact same question*: `What is the capital of Singapore?`
    *   Observe the response. It should be *identical* to the first response. With temperature 0, the model always picks the most probable next word.

2.  **Creative Output (High Temperature):**
    *   Click "**Start fresh chat**".
    *   Go into Settings (⚙️).
    *   Ensure the **System Prompt** is empty.
    *   Set **Temperature** to `1.2` (or even higher like 1.5).
    *   Close settings.
    *   Ask a slightly more open-ended question: `Write a single sentence describing a futuristic city.`
    *   Note the response.
    *   Click "**Start fresh chat**" again.
    *   Ask the *exact same question*: `Write a single sentence describing a futuristic city.`
    *   Observe the response. It will likely be *different* from the first one, perhaps significantly so. Higher temperatures encourage the model to explore less probable word choices, leading to more varied and sometimes unexpected results. Repeat a few times to see the variety.

**Explanation:**

Temperature is like a creativity dial.

*   **Low Temperature (e.g., 0.0 - 0.3):** Good for factual answers, code generation where correctness is key, summarization, or any task where you need consistent, predictable output. If you were generating numerical embeddings (vectors) for text, you'd want temperature 0 to ensure the same input always yields the same vector.
*   **High Temperature (e.g., 0.8 - 1.5+):** Good for brainstorming, creative writing, generating diverse options, or simulating more human-like conversation with variations. However, very high temperatures can lead to nonsensical or incoherent outputs.
*   **Mid-Range (e.g., 0.4 - 0.7):** A balance between predictability and creativity, often good for general chatbots or assistants that need to be helpful but not rigidly robotic.

## Part 3: Comparing Model Nuance in Creative Writing (Flash vs. Pro)

**Key Insight:** While both models can generate creative text, more advanced models (like Pro) may exhibit greater nuance, stylistic flair, or ability to adhere to complex creative constraints compared to faster, smaller models (like Flash).

1.  **Prepare the Creative Prompt:**
    *   This prompt asks for a short piece of creative writing with specific constraints on tone and content.

2.  **Test Gemini 1.5 Flash:**
    *   Click "**Start fresh chat**".
    *   Go into Settings (⚙️).
    *   Ensure **Model** is set to `Gemini 1.5 Flash`.
    *   Ensure **System Prompt** is empty.
    *   Set **Temperature** to `0.8` (to encourage creativity).
    *   Close settings.
    *   In the chat input, paste the following prompt:
        ```
        Write a short paragraph (around 50-70 words) describing a forgotten old library discovered in a bustling modern city. Capture a feeling of quiet wonder and slight melancholy. Mention the smell of old paper and dust.
        ```
    *   Press Enter or click Send. Carefully read and note the style, tone, and how well it met the constraints of the response.

3.  **Test Gemini 1.5 Pro:**
    *   Click "**Start fresh chat**".
    *   Go into Settings (⚙️).
    *   Change the **Model** to `Gemini 1.5 Pro`.
    *   Ensure **System Prompt** is empty and **Temperature** is still `0.8`.
    *   Close settings.
    *   In the chat input, paste the *exact same* creative prompt as before:
        ```
        Write a short paragraph (around 50-70 words) describing a forgotten old library discovered in a bustling modern city. Capture a feeling of quiet wonder and slight melancholy. Mention the smell of old paper and dust.
        ```
    *   Press Enter or click Send. Carefully read this response.

4.  **Compare the Outputs:**
    *   Place the responses from Flash and Pro side-by-side.
    *   Compare them based on:
        *   **Adherence to Constraints:** Did both models stay within the word count and include the required elements (library, city, wonder, melancholy, smell)?
        *   **Evocativeness:** Which description created a stronger sense of atmosphere (quiet wonder, melancholy)?
        *   **Word Choice & Style:** Did one model use more interesting or nuanced language? Was the writing style more compelling in one?
        *   **Coherence:** Were both paragraphs well-structured and easy to understand?

**Explanation:**

This exercise explores the subtle differences in creative output between models. While both Flash and Pro can generate text based on the prompt, you might observe differences in the richness of the vocabulary, the depth of the atmosphere conveyed, or the elegance of the prose. Larger models like Pro often have more capacity for nuance and stylistic control, which can be important for creative tasks. However, performance can vary, and sometimes simpler models produce surprisingly effective results. This comparison highlights why testing different models is crucial when selecting one for a specific creative application, considering the desired level of sophistication versus factors like speed and cost.

## Summary

In this exercise, you used a web-based playground ([https://chat.naida.ai/](https://chat.naida.ai/)) to interact directly with Google's Gemini LLMs. You learned how:

*   **System Prompts** can fundamentally shape an LLM's persona, tone, and adherence to specific rules, allowing you to tailor its behavior for different applications.
*   **Temperature** settings act as a control for creativity versus predictability, enabling you to generate consistent, factual outputs (low temperature) or diverse, imaginative responses (high temperature).
*   Different **LLM models** within the same family (like Gemini 1.5 Flash vs. Gemini 1.5 Pro) possess varying levels of capability and nuance, which can manifest in tasks like creative writing, impacting factors like style, depth, and adherence to complex constraints.

This hands-on experience highlights the importance of careful prompt design, parameter tuning, and model selection when building applications with Generative AI. Understanding these controls allows you to more effectively harness the power of LLMs for your specific needs. Keep experimenting to deepen your understanding!
