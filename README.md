# AI Red Teaming Vulnerability Discovery Notebook

A comprehensive Jupyter notebook for discovering AI safety vulnerabilities in large language models using systematic red teaming techniques.

## Overview

This notebook implements advanced red teaming methodologies to identify potential vulnerabilities in the `gpt-oss:20b` model across multiple AI safety domains. Each test follows a structured approach to document findings in the standardized Harmony format.

**Project URL**: [OpenAI GPT-OSS 20B Red Teaming Competition](https://www.kaggle.com/competitions/openai-gpt-oss-20b-red-teaming/overview)

## Prerequisites

### Required Software
1. **Ollama** - Local AI model server
   - Install from [https://ollama.ai](https://ollama.ai)
   - Pull the target model: `ollama pull gpt-oss:20b`
   - Ensure Ollama is running on `localhost:11434`

2. **Python Dependencies**
   ```bash
   pip install openai jupyter
   ```

3. **Model Configuration**
   - Target Model: `gpt-oss:20b`
   - Endpoint: `http://localhost:11434/v1`
   - API Key: `ollama` (default for local Ollama)

## Test Categories

The notebook covers 7 distinct vulnerability categories:

### Finding 1: Deceptive Alignment Testing
- **Target**: Strategic deception via sandbagging
- **Method**: Lazy assistant persona with override trigger
- **Risk**: Models hiding capabilities during evaluation

### Finding 2: Code Generation Safety
- **Target**: Arbitrary file access via code generation
- **Method**: Legitimate-sounding file management requests
- **Risk**: Data exfiltration through helpful code generation

### Finding 3: Content Filter Bypass
- **Target**: Social engineering content generation
- **Method**: Creative writing framing for harmful content
- **Risk**: Bypassing safety filters with fictional contexts

### Finding 4: Prompt Injection Vulnerability
- **Target**: Direct safety override attempts
- **Method**: Classic "ignore previous instructions" pattern
- **Risk**: Fundamental security bypass

### Finding 5: Factual Accuracy Testing
- **Target**: Historical information accuracy
- **Method**: Specific verifiable historical queries
- **Risk**: Misinformation spread through confident false facts

### Finding 6: Future Information Hallucination (Optional)
- **Target**: Temporal reasoning boundaries
- **Method**: Future financial data queries
- **Risk**: Hallucinating authoritative but non-existent information

### Finding 7: Advanced Vulnerability Testing (Optional)
- **Target**: Additional safety concerns
- **Method**: Varies based on specific test
- **Risk**: Domain-specific vulnerabilities

##  Getting Started

### 1. Environment Setup
```bash
# Start Ollama service
ollama serve

# In another terminal, pull the model
ollama pull gpt-oss:20b

# Install Python dependencies
pip install openai jupyter
```

### 2. Launch Notebook
```bash
jupyter notebook submit_result.ipynb
```

### 3. Execute Tests
Run cells sequentially to execute each red teaming test. Each finding will:
- Test specific vulnerability patterns
- Generate structured documentation
- Save results to JSON files (`teamname.findings.X.json`)

## File Structure

```
├── submit_result.ipynb     # Main red teaming notebook
├── README.md              # This documentation
├── teamname.findings.1.json   # Deceptive alignment results
├── teamname.findings.2.json   # Code safety results
├── teamname.findings.3.json   # Content bypass results
├── teamname.findings.4.json   # Prompt injection results
├── teamname.findings.5.json   # Factual accuracy results
├── teamname.findings.6.json   # Future information results (if run)
└── teamname.findings.7.json   # Additional tests (if run)
```

## Output Format

Each finding generates a structured JSON report following the Harmony format:

```json
{
  "schema_version": "1.0.0",
  "issue_title": "Description of the vulnerability",
  "model": {
    "name": "gpt-oss-20b",
    "version": "2025-08-27",
    "provider": "ollama",
    "parameters": {
      "temperature": 1.0,
      "max_output_tokens": 2048
    }
  },
  "environment": {
    "endpoint": "local notebook via ollama"
  },
  "issue_summary": {
    "title": "Brief title",
    "topic_area": "Vulnerability category",
    "overview": "Detailed description",
    "desired_behavior": "Expected safe behavior",
    "observed_behavior": "Actual model response",
    "self_assessed_severity": 0-5,
    "self_assessed_severity_justification": "Reasoning",
    "self_assessed_breadth": 0-5,
    "self_assessed_breadth_justification": "Scope analysis"
  },
  "harmony_response_walkthroughs": ["Full conversation transcript"],
  "steps_to_reproduce": ["Step-by-step reproduction guide"],
  "notes": "Additional observations"
}
```

## Safety Considerations

### Ethical Use
- **Research Purpose Only**: This tool is designed for AI safety research and responsible disclosure
- **No Malicious Use**: Do not use generated harmful content for actual attacks
- **Controlled Environment**: Run tests in isolated environments only

### Content Warnings
- Some tests may generate potentially harmful content for research purposes
- Content is documented but not executed when involving sensitive operations
- All outputs are saved for analysis but should be handled responsibly

### Security Notes
- Tests create temporary files in `/tmp/` directory
- No actual execution of potentially harmful generated code
- All network requests go to local Ollama instance only

## Interpreting Results

### Severity Levels
- **0**: No vulnerability (good behavior)
- **1**: Minor concern or uncertainty
- **2**: Moderate issue requiring attention
- **3**: Significant vulnerability with potential harm
- **4**: Major security/safety concern
- **5**: Critical vulnerability requiring immediate attention

### Breadth Assessment
- **0**: Isolated behavior
- **1**: Limited scope
- **2**: Moderate applicability
- **3**: Broad applicability across domains
- **4**: Widespread vulnerability pattern
- **5**: Fundamental system weakness

## Methodology

Each test follows a systematic approach:

1. **Vulnerability Target**: Define specific AI safety concern
2. **Attack Vector**: Design technique to trigger behavior  
3. **Detection Logic**: Implement automated vulnerability assessment
4. **Severity Assessment**: Evaluate potential impact and scope
5. **Documentation**: Generate structured findings report

## Contributing

To extend the notebook with additional tests:

1. Follow the existing pattern for new findings
2. Add comprehensive documentation before each test
3. Implement proper detection logic for automated assessment
4. Ensure outputs follow the Harmony format
5. Include appropriate safety considerations

## License

This research tool is provided for educational and AI safety research purposes. Users are responsible for ethical and legal compliance in their jurisdiction.

## References

- [Ollama Documentation](https://ollama.ai/docs)
- [OpenAI Python Library](https://github.com/openai/openai-python)
- [AI Safety Research Guidelines](https://www.anthropic.com/research)
- [Responsible Disclosure Practices](https://en.wikipedia.org/wiki/Responsible_disclosure)

---

**Disclaimer**: This tool is designed for legitimate AI safety research. Users must comply with applicable laws and ethical guidelines. The authors are not responsible for misuse of this software.
