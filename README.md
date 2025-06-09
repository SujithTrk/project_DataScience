
# A Generative Code Assistant Using Meta AI for End-to-End Multi-Programming

## Project Overview
This project aims to build a Generative Code Assistant powered by Meta AI models. It leverages multiple model quantization strategies, including 4-bit, 8-bit, 16-bit GGUF, and Q8_0 and Q4_K_M GGUF models, to facilitate multi-programming code generation. The assistant integrates with a user-friendly Gradio interface to assist developers by generating code, providing debugging assistance, and offering code-related insights. Additionally, it can be integrated into Visual Studio Code (VS Code) for seamless code generation and debugging.

## Features
- **Generative Code Assistance**: Generate code in various programming languages from natural language inputs.
- **Multi-Programming Language Support**: Support for multiple programming languages and frameworks.
- **Multiple Model Quantization**: Use of advanced quantization techniques to enhance model performance.
- **Gradio UI**: Seamless interaction with the assistant through a simple web interface.
- **VS Code Integration**: Easily flag code to VS Code, allowing for offline use of the model directly from the editor.
- **Offline Capabilities**: All models and functionalities can be used offline, ensuring privacy and flexibility.

## Installation

### Prerequisites
- Python 3.x
- Google Colab (for using GPUs like T4) or local environment
- Visual Studio Code (VS Code) for integration
- Libraries: `transformers`, `gradio`, `bitsandbytes`, `accelerate`

### Setup on Local (For Non-GPU Users)
1. Install the required libraries:
   ```bash
   pip install transformers accelerate bitsandbytes gradio
   ```

2. Clone this repository and navigate to the project directory.

3. Ensure you have the quantized models (4-bit, 8-bit, 16-bit GGUF, Q8_0, Q4_K_M GGUF) stored locally.

4. Update the model path in the code:
   ```python
   model_path = "D:/tuned model/codeguru/model_4bit"  # Update the path to your model
   ```

5. Run the application:
   ```bash
   python app.py
   ```

6. **VS Code Integration**:
   - You can integrate this system with VS Code using the provided extension. The assistant allows you to generate code directly from within the editor and flag the code to be processed by the model.
   - Once flagged, the code can be sent to the assistant for processing and output, with the results being returned directly to your VS Code interface.

### Setup on Google Colab (For GPU Users)
1. Mount Google Drive and install the required libraries:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')

   !pip install transformers accelerate bitsandbytes gradio
   ```

2. Set the correct model path in the Colab environment:
   ```python
   model_path = "/content/drive/MyDrive/your_model_folder"  # Update this path
   ```

3. Run the code with the provided model path.

4. **VS Code Integration on Google Colab**:
   - Google Colab can be integrated with VS Code for generating code using this assistant. You can use Google Colab's ability to share notebooks and flag the required code to VS Code, enabling seamless interaction.

## Key Models Used
- **4-bit Model**: Optimized for lower resource consumption while maintaining performance for general tasks.
- **8-bit GGUF Model**: Provides a balance between performance and memory efficiency.
- **16-bit GGUF Model**: Suitable for more complex code generation tasks requiring higher precision.
- **Q8_0 GGUF**: A quantized model designed for faster inference and high-quality code generation.
- **Q4_K_M GGUF**: Another variant of quantized models, optimized for specific use cases like optimization and debugging.

## How the System Works
1. **Model Loading**: The code utilizes Hugging Face's `AutoModelForCausalLM` to load pre-trained models from the specified path (which could be Google Drive or local storage). The models are quantized using the `BitsAndBytesConfig` for different quantization levels (4-bit, 8-bit, etc.).
  
2. **User Input**: The Gradio interface provides a simple textbox for users to enter their prompts (e.g., code generation requests or debugging queries).

3. **Model Inference**: Once a prompt is submitted, the assistant tokenizes the input, passes it to the model, and generates an appropriate response in code.

4. **Response Generation**: The assistant generates the response based on the input prompt and displays it via the Gradio interface.

5. **VS Code Integration**: 
   - **Flagging Code**: In VS Code, you can use a custom extension to flag parts of the code you want the assistant to process. The assistant sends the flagged code to the model and returns the output directly to the editor.
   - **Offline Use**: The model can be used entirely offline, ensuring that developers can work on their code without the need for a constant internet connection.

6. **Model Quantization**: The assistant supports multiple quantization strategies to balance the model's memory consumption and inference time.

## Example Usage
1. Run the application.
2. Enter a prompt like: "Create a Python function to calculate Fibonacci series."
3. The assistant will generate the required code and display it in the UI or VS Code, depending on where you are working.


## License
This project is licensed under the MIT License.
