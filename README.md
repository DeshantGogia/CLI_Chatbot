# Chatbot CLI with Memory

A conversational AI chatbot built with Hugging Face Transformers that includes memory capabilities for maintaining context across conversations. This project provides both a Jupyter notebook interface and a command-line interface for interactive conversations.

## Features

- **🧠 Memory System**: Sliding window memory that keeps track of recent conversation history
- **🎯 Context Awareness**: Uses conversation history to provide more relevant responses
- **🖥️ Interactive Interface**: Jupyter widgets for easy interaction in notebooks
- **⚡ GPU Support**: Optimized for CUDA-enabled systems
- **🔧 Response Cleaning**: Filters out unwanted dialogue formats and Q&A patterns
- **📊 Memory Management**: Functions to view, clear, and manage conversation history

## Requirements

- Python 3.8+
- CUDA-compatible GPU (recommended)
- 4GB+ RAM
- 2GB+ free disk space

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd chatbot_cli
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Launch Jupyter Notebook:
```bash
jupyter notebook
```

4. Open `model_loader.ipynb` and run the cells in order.

## Usage

### Jupyter Notebook Interface

1. Run all cells in the notebook in order
2. Use the interactive widget interface that appears at the bottom
3. Type your messages in the text input field
4. Click "Send" to get responses
5. Use "Clear Memory" to reset conversation history
6. Use "Memory Status" to check current memory state

### Programmatic Usage

```python
from transformers import pipeline

# Initialize chatbot
chatbot = ChatbotWithMemory(max_history=6)

# Chat with the bot
response = chatbot.chat("Hello, how are you?")
print(response)

# Check memory status
chatbot.show_memory_status()

# Clear memory
chatbot.clear_history()
```

## Model Information

- **Default Model**: TinyLlama/TinyLlama-1.1B-Chat-v1.0
- **Model Size**: ~1.1B parameters
- **Memory Usage**: ~2GB VRAM
- **Context Length**: 2048 tokens
- **Memory Window**: 6 conversation turns (configurable)

## Configuration

### Memory Settings
- `max_history`: Maximum number of conversation turns to keep (default: 6)
- Adjust based on your GPU memory and desired context length

### Model Parameters
- `max_new_tokens`: Maximum tokens to generate (default: 100)
- `temperature`: Controls randomness (default: 0.7)
- `top_p`: Nucleus sampling parameter (default: 0.9)
- `repetition_penalty`: Reduces repetition (default: 1.1)

## Troubleshooting

### Common Issues

1. **CUDA Out of Memory**
   - Reduce `max_history` parameter
   - Use a smaller model
   - Close other GPU-intensive applications

2. **Slow Response Times**
   - Ensure CUDA is properly installed
   - Check GPU utilization
   - Consider using a more powerful GPU

3. **Poor Response Quality**
   - Adjust temperature and top_p parameters
   - Try different models
   - Increase max_new_tokens

### System Requirements Check

Run the first cell in the notebook to verify your system:
```python
import torch
print("Torch version:", torch.__version__)
print("CUDA available:", torch.cuda.is_available())
```

## File Structure

```
chatbot_cli/
├── model_loader.ipynb    # Main Jupyter notebook
├── requirements.txt      # Python dependencies
└── README.md            # This file
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.

## Acknowledgments

- Hugging Face Transformers library
- TinyLlama model by Meta
- Jupyter widgets for the interactive interface
