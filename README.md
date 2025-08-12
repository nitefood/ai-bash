# AI - a commandline LLM chat client in BASH with conversation/completion and image generation support

## Features:

* **Supports any OpenAI-compatible API endpoint, both local and remote**

  * _[OpenAI](https://platform.openai.com/docs/)_
  * _[Gemini](https://aistudio.google.com/)_
  * _[Grok](https://x.ai/api)_
  * _[HuggingFace](https://huggingface.co/docs/api-inference/index)_
  * _[OpenRouter](https://openrouter.ai/docs/quick-start)_
  * _[LM Studio](https://lmstudio.ai/docs/api/openai-api)_
  * _[Ollama](https://ollama.com/blog/openai-compatibility)_
  * _and many more_

* **Interactive chat sessions**

* **Multiline input**

* **Image generation support:** *(currently limited to DALL·E 2)*
  
  * _image preview grid rendered directly in the terminal_
  * _generate up to 10 images at a time_
  * _automatic URL shortening_
  * _optionally save images and prompt to local disk_

* **Markdown support for replies** (requires [glow](https://github.com/charmbracelet/glow#installation))

* **Single turn Q&A** with optional follow-up conversation

* **Data piping support** (sending file contents to the LLM)

* **Full conversation support**:
  
  * _locally store unlimited conversations (in JSON format)_
  * _quick resume last conversation_
  * _delete/resume any stored conversation_
  * _conversation messages replay on resume_
  * _store current and start new conversation (reset history) during interactive sessions_
  * _Automatic conversation topic identification and update_

* **Multiple chat models support**:

  * _switch to a different model mid-conversation_
  * _can freely combine local and remote models_
  * _a single tool to query any model served through an OpenAI-compatible API endpoint_

* **Multiple system prompt support**:

  * _manage multiple system prompts to alter the base model behavior and persona_

## Full command line options (`ai -h`):

###### Manage models (add/delete/set default):

  `ai -m`

###### Start a new interactive conversation:

`ai [-m <modelname>]`

###### Single turn Q&A (will ask you to continue interacting, otherwise quit after answer):

`ai [-m <modelname>] "how many planets are there in the solar system?"`

###### Generate one or more images (default 1, max 10):

`ai -i [num] "a cute cat"`

###### Submit data as part of the question:

`cat file.txt | ai [-m <modelname>] can you summarize the contents of this file?`

###### List saved conversations:

`ai -l`

###### Continue last conversation:

`ai -c`

###### Continue specific conversation:

`ai -c <conversation_id>`

###### Delete a specific conversation:

`ai -d <conversation_id>`

###### Delete selected conversations:

`ai -d <conversation_id_start>-<conversation_id_end>`

###### Delete all conversations:

`rm "$HOME/.config/ai-bash/conversations.json"`

## Usage examples:

##### (Adding a model)

![image](https://github.com/user-attachments/assets/acd404d6-1766-4764-a590-bceb04bb3696)

##### (Listing added models)

![image](https://github.com/user-attachments/assets/feace719-0308-4e6a-8a03-f1f21d941378)

##### (Interaction and conversation resuming)

[![asciicast](https://asciinema.org/a/572784.svg)](https://asciinema.org/a/572784)

##### (Image generation)

[![asciicast](https://asciinema.org/a/572785.svg)](https://asciinema.org/a/572785)

##### (Input piping to stdin)

[![asciicast](https://asciinema.org/a/572786.svg)](https://asciinema.org/a/572786)

## Installation:

###### Prerequisites:

* Install jq, curl, imagemagick, catimg
  
  * for e.g. Ubuntu: `apt -y install jq curl imagemagick catimg`

* Install [glow](https://github.com/charmbracelet/glow#installation) for Markdown rendering support in your terminal

###### Script download:

Install the script by either cloning this repository or directly downloading to your `$PATH`, e.g.:

```shell
curl "https://raw.githubusercontent.com/nitefood/ai-bash/master/ai" > /usr/bin/ai && chmod 0755 /usr/bin/ai
```
