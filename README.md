# Alpaca.cpp

Run a fast ChatGPT-like model locally on your device. The screencast below is not sped up and running on an M2 Macbook Air with 4GB of weights. 

[![asciicast](screencast.gif)](https://asciinema.org/a/dfJ8QXZ4u978Ona59LPEldtKK)

This combines the [LLaMA foundation model](https://github.com/facebookresearch/llama) with an [open reproduction](https://github.com/tloen/alpaca-lora) of [Stanford Alpaca](https://github.com/tatsu-lab/stanford_alpaca) a fine-tuning of the base model to obey instructions (akin to the [RLHF](https://huggingface.co/blog/rlhf) used to train ChatGPT)... 

## Get Started (7B)

Download the zip file corresponding to your operating system from the [latest release](https://github.com/antimatter15/alpaca.cpp/releases/latest). On Windows, download `alpaca-win.zip`, on Mac (both Intel or ARM) download `alpaca-mac.zip`, and on Linux (x64) download `alpaca-linux.zip`. 

Download `ggml-alpaca-7b-q4.bin` and place it in the same folder as the `chat` executable in the zip file. There are several options: 

Once you've downloaded the model weights and placed them into the same directory as the `chat` executable, run:

```
./chat
```

A one endpoint API has been added to the prompt type mode, chat mode is removed and the model stays in memory until the app is killed forcefully. 
There is no need to pass some of the params, threads, top k, top p, temp can be provided in query string of API call, unless you stick with one value, then feel free to set on launch.
Once it's running you can post text/plain to localhost:4200?top_k=30&t=7 if you want 7 threads, for example. Omitting all query params leads to default values as set in original alpaca repo.

## Building from Source (MacOS/Linux)

You will probabbly need to install libboost dev as it is needed for crow lib.

```sh
git clone https://github.com/gruzinskis/alpaca.cpp/tree/gljuks/apiserve-singleprompt
cd alpaca.cpp

make chat
./chat
```

missing gglm clear on shutdown, but isn't really an issue for testing.
