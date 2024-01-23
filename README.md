# Speech Synthesis with Mamba

This the notebook presented in [Lukas Nel's blog](https://2084.substack.com/p/2084-marcrandbot-speech-synthesis) ported to the Determined AI platform, using Detached mode, with a few minor changes:

- Performing some of the audio preprocessing steps using ffmpeg instead of moviepy
- Padding the audio snippets with 0s or truncating if the snippet is not exactly 10s
- Using the unconditional generation function provided rather than generating from test audio samples (as shown in the blog)
- Using Determined AI's Detached Mode for visualization and checkpointing instead of Weights & Biases

This script trains a Mamba model on audio snippets from a YouTube video or playlist link. After the model is trained, it generates new audio using a model checkpoint. 

Currently, the model overfits during training, so the output is usually not high quality, but the model sometimes memorizes training data and outputs cool sounding memorized audio 😎

Possible causes for this are small dataset sizes + generation without a seed audio. These possibilities are currently under investigation 🔍

# How to run:

1) Install Determined AI on any platform
2) Open the Web UI and launch JupyterLab
3) Set the environment to `determinedai/environments:cuda-11.8-pytorch-2.0-gpu-0.26.5` in "Advanced Configuration Settings"
4) Change filepath variables at the top of the notebook to match your filesystem and desired audio generation settings (YouTube link, folder names for downloaded audio + snippets).
5) After the model is trained, in Section "Test out model", change the checkpoint directory to your desired checkpoint before generating new audio.
   



