# AI - a commandline LLM chat client in BASH with conversation/completion and image generation support

## Features:

* **Supports any OpenAI-compatible API endpoint, both local and remote** *e.g. OpenAI, Gemini, LM Studio, Ollama, and more*

* **Interactive chat sessions**

* **Multiline input**

* **Image generation support:** *(currently limited to DALL·E 2)*
  
  * image preview grid rendered directly in the terminal
  
  * generate up to 10 images at a time
  
  * automatic URL shortening
  
  * optionally save images and prompt to local disk

* **Markdown support for replies** (requires [glow](https://github.com/charmbracelet/glow#installation))

* **Single turn Q&A** with optional follow-up conversation

* **Data piping support** (sending file contents to the LLM)

* **Full conversation support**:
  
  * locally store unlimited conversations (in JSON format)
  
  * quick resume last conversation
  
  * delete/resume any stored conversation
  
  * conversation messages replay on resume
  
  * store current and start new conversation (reset history) during interactive sessions
  
  * Automatic conversation topic identification and update

* **Multiple chat models support**:

  * switch to a different model mid-conversation
  * can freely combine local (open source) and remote (closed) models
  * a single tool to query any model served through an OpenAI-compatible API endpoint

## Full command line options (`ai -h`):

###### Start a new interactive conversation:

`ai`

###### Single turn Q&A (will ask you to continue interacting, otherwise quit after answer):

`ai "how many planets are there in the solar system?"`

###### Generate one or more images (default 1, max 10):

`ai -i [num] "a cute cat"`

###### Submit data as part of the question:

`cat file.txt | ai can you summarize the contents of this file?`

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

`rm "$HOME/conversations.json"`

###### Manage models:

  `ai -m list`

  `ai -m add` *(opens the model adding wizard, which includes various presets)*
  
  `ai -m add <model_name> <endpoint> <api_key> [default]`

  `ai -m delete <model_name>`

  `ai -m setdefault <model_name>`

## Usage examples:

##### (Adding a model)

![image](https://github.com/user-attachments/assets/ae38f968-b1bc-402b-99cd-1a8680d92ab7)

##### (Listing added models)

![image](https://github.com/user-attachments/assets/6fcca44c-5b87-4204-8b2a-56aedfafad61)

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
