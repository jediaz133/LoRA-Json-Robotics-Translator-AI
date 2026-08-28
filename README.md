## Model Description
This model was trained using LoRA on milistu's robot-instructions dataset.
It's main objective is to translate a person's request into a json string which can be interpreted to run/observe motors/sensors.

### Example
User: Get the tempurature reading of the Radioactive Core's twelfth rod"

Response: [{"function": "get_temperature", "kwargs": {"rod": 12}}]

## Usage In Notebook file

After training the model yourself you can then use the genRobotics(question,  maxNewTokens=220) function
example being genRobotics("move joint 10 by 90 degrees")


## Files
A Jupyter Notebook to train Microsoft's Phi 3 Mini 4k Instructs model.
A folder where the Lora AdapterSets are saved

## Notes
This was model was trained on an AMD RX 6700xt GPU. Because of this some environment variables were set with "HSA_OVERRIDE_GFX_VERSION" = "10.3.0" being the most important.

milistu's robot-instructions dataset: https://huggingface.co/datasets/milistu/robot-instructions

## Issues
Sometimes the model will respond in radians rather than degrees for motor/joint motion requests.


There's a portion at the end where multiple combinations of parameters are tested. On an online rental nVidia 5070 ti it worked fine however on my local hardware it doesn't really work.
