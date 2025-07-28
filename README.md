# 🎯 Setwise VSCode Extension

**Professional LaTeX quiz generation with live preview and advanced templating directly in VSCode.**

[![VSCode](https://img.shields.io/badge/VSCode-Extension-blue.svg)](https://marketplace.visualstudio.com/items?itemName=setwise.setwise-questions)
[![Python](https://img.shields.io/badge/Python-3.8%2B-green.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Transform VSCode into a powerful quiz authoring environment with intelligent LaTeX support, live preview, and v2.0 templated question features.

## ✨ Key Features

::: {.grid}

### 📝 Smart Question Editing
- **Advanced syntax highlighting** for `.py` question files with LaTeX math support
- **IntelliSense & auto-completion** for question structures and LaTeX commands
- **Rich snippet library** (mcq, subjective, templated questions, physics, chemistry)
- **Real-time validation** with instant error highlighting and helpful suggestions
- **🆕 v2.0 Template Support** - Full support for templated MCQ and subjective questions

### 🔍 Live Preview & Generation
- **One-click PDF preview** with live compilation in VSCode
- **Multi-set generation** with configurable parameters (sets, questions, seed)
- **Template selection** (default, compact, minimal) with live switching
- **🆕 Quiz metadata** - Professional headers with title, duration, instructions
- **Answer key generation** with detailed solutions

### 🔧 LaTeX Intelligence
- **Automatic error fixing** - Instantly fix common LaTeX mistakes (missing $, chemical formulas)
- **Smart validation** with user-friendly error messages instead of cryptic LaTeX errors
- **Interactive LaTeX help** with syntax reference and live examples
- **Chemical formula support** - Auto-convert H2O → H$_2$O, CO2 → CO$_2$
- **Math expression assistance** - Auto-wrap expressions in $ delimiters

### 📊 Advanced Question Management
- **File statistics** - Question counts, total marks, validation status, template usage
- **🆕 Template variable tracking** - See which questions use dynamic variables
- **Question library management** - Import, export, and organize question collections
- **Multi-part question support** - Enhanced editing for complex questions with individual marks

## 🚀 Quick Start

### 1. Install the Extension
```bash
# From VSCode Extensions marketplace
# Search for "Setwise Quiz Generator"
# Or install from command line:
code --install-extension setwise.setwise-questions
```

### 2. Setup Prerequisites
```bash
# Install Setwise CLI
pip install git+https://github.com/nipunbatra/setwise.git

# Verify installation
setwise --help
```

### 3. Create Your First Quiz

1. **Create a new file:** `my_quiz.py`
2. **Use snippets** for rapid development:
   - Type `quiz-meta` + Tab → Add v2.0 quiz metadata
   - Type `mcq-template` + Tab → NEW templated MCQ question
   - Type `mcq` + Tab → Regular MCQ question
   - Type `subjective` + Tab → Subjective question
   - Type `multi-part` + Tab → Multi-part question

3. **Live Preview:**
   - Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
   - Select "Setwise: Preview Quiz"
   - PDF opens instantly in VSCode!

4. **Generate Multiple Sets:**
   - Press `Ctrl+Shift+G` to generate multiple randomized quiz sets
   - Choose template (default/compact/minimal) and number of sets
   - All PDFs and answer keys generated automatically

### 4. Explore v2.0 Features

**NEW Templated MCQ Questions:**
```python
# Type 'mcq-template' + Tab to get this:
{
    "template": r"Calculate {{ a }} × {{ b }} = ?",
    "options": [
        r"{{ a * b }}",      # Correct
        r"{{ a + b }}",      # Common mistake
        r"{{ a - b }}",      # Wrong operation
        r"{{ a / b if b != 0 else 'undefined' }}"
    ],
    "answer": r"{{ a * b }}",
    "variables": [
        {"a": 6, "b": 7},   # 42
        {"a": 8, "b": 9},   # 72
        {"a": 4, "b": 5}    # 20
    ],
    "marks": 2
}
```

## 🎮 Commands & Keybindings

### 🎯 Main Commands

| Command | Shortcut | Description |
|---------|----------|-------------|
| **Setwise: Preview Quiz** | `Ctrl+Shift+P` / `Cmd+Shift+P` | Generate single PDF preview |
| **Setwise: Generate Quiz Sets** | `Ctrl+Shift+G` / `Cmd+Shift+G` | Generate multiple randomized sets |
| **Setwise: Validate Questions** | `Ctrl+Shift+V` / `Cmd+Shift+V` | Check syntax and LaTeX |
| **Setwise: Live Preview Mode** | `Ctrl+Shift+L` / `Cmd+Shift+L` | Toggle auto-preview on save |

### 🔧 LaTeX Tools

| Command | Description |
|---------|-------------|
| **Setwise: Fix LaTeX Errors** | Auto-fix common LaTeX mistakes (missing $, chemical formulas) |
| **Setwise: LaTeX Help** | Interactive LaTeX syntax reference with examples |
| **Setwise: Show File Statistics** | Display question counts, marks, template usage |
| **Setwise: Validate Templates** | Check templated questions for variable consistency |

### ➕ Quick Insert Templates

| Snippet | Result |
|---------|--------|
| `quiz-meta` | v2.0 quiz metadata dictionary |
| `mcq-template` | 🆕 Templated MCQ with variables |
| `mcq` | Regular MCQ question |
| `subjective` | Subjective question |
| `multi-part` | Multi-part question with individual marks |
| `physics-template` | Physics equation with variables |
| `chem-template` | Chemistry equation template |
| `math-template` | Mathematical expression template |

## ⚙️ Configuration

**Access via:** File → Preferences → Settings → Search "Setwise"

```json
{
    // 🔄 Live Features
    "setwise.autoPreview": true,              // Auto-preview when opening .py files
    "setwise.autoValidate": true,             // Auto-validate on save
    "setwise.livePreview": false,             // Live preview on every keystroke (resource intensive)
    
    // 🎨 Quiz Generation
    "setwise.defaultTemplate": "default",     // Default template: default/compact/minimal
    "setwise.previewSets": 1,                 // Number of sets for preview (1-3 recommended)
    "setwise.defaultSeed": null,              // Default random seed (null = random)
    
    // 🔧 LaTeX Intelligence
    "setwise.autoFixLatex": true,             // Auto-fix LaTeX errors on save
    "setwise.latexHelpLevel": "detailed",     // Help detail: basic/detailed/expert
    "setwise.chemicalFormulaFix": true,       // Auto-convert H2O → H$_2$O
    
    // 📊 Interface
    "setwise.showStatistics": true,           // Show file statistics in status bar
    "setwise.enableIntelliSense": true,       // Enable auto-completion
    "setwise.syntaxHighlighting": "enhanced", // LaTeX syntax highlighting level
    
    // 📁 File Management
    "setwise.outputDirectory": "./output",    // Default output directory
    "setwise.backupOnSave": false,           // Backup questions file before fixing
    "setwise.templateLibraryPath": null       // Custom template library location
}
```

## File Structure

Create question files with this structure:

```python
# Multiple Choice Questions
mcq = [
    {
        "question": r"What is $2 + 2$?",
        "options": [
            r"3",
            r"4", 
            r"5",
            r"6"
        ],
        "answer": r"4",
        "marks": 1
    }
]

# Subjective Questions
subjective = [
    {
        "question": r"Derive the quadratic formula.",
        "answer": r"Starting from $ax^2 + bx + c = 0$...",
        "marks": 5
    }
]
```

## LaTeX Support

The extension provides comprehensive LaTeX support:

### Auto-fixes Applied
- Missing `$` delimiters: `x^2` → `$x^{2}$`
- Chemical formulas: `H2O` → `H$_2$O`
- Special characters: `%` → `\\%`
- Degree symbols: `45 degrees` → `45°`

### Syntax Highlighting
- **Math expressions** in `$...$` are highlighted
- **LaTeX commands** like `\frac`, `\sqrt` are recognized
- **Chemical formulas** and **subscripts** are styled
- **Question structure** keywords are emphasized

## Templates and Snippets

### 🎨 Complete Snippet Library

#### 📋 Question Types
- `quiz-meta` - 🆕 v2.0 Quiz metadata with title, duration, instructions
- `mcq-template` - 🆕 Templated MCQ with dynamic variables
- `mcq` - Standard multiple choice question
- `subjective` - Subjective question with detailed answer
- `multi-part` - 🆕 Multi-part question with individual marks
- `template-subj` - 🆕 Templated subjective question

#### 🔬 Subject-Specific Templates
- `physics-template` - Physics equation with variables (projectile, energy, etc.)
- `chemistry-template` - Chemical equation balancing with variables
- `math-template` - Mathematical expressions with dynamic values
- `cs-template` - Computer science concepts with parameters

#### 🧮 LaTeX Math Helpers
- `math` - Math expression wrapper: `$...$`
- `frac` - LaTeX fraction: `\frac{numerator}{denominator}`
- `sqrt` - Square root: `\sqrt{expression}`
- `integral` - Integral: `\int_{lower}^{upper} expression \, dx`
- `matrix` - Matrix: `\begin{pmatrix} ... \end{pmatrix}`
- `equation` - Equation environment: `\begin{equation} ... \end{equation}`

#### 🧪 Chemistry Helpers
- `chem` - Chemical formula: H$_2$O, CO$_2$, etc.
- `reaction` - Chemical reaction: A + B → C + D
- `equilibrium` - Chemical equilibrium: A ⇌ B
- `ion` - Ion notation: Na$^+$, Cl$^-$

#### ⚡ Quick Inserts
- `degree` - Degree symbol: °
- `infinity` - Infinity: ∞
- `pm` - Plus/minus: ±
- `approx` - Approximately: ≈
- `arrow` - Right arrow: →
- `therefore` - Therefore: ∴

### Template Variables
Create dynamic questions:

```python
{
    "template": r"Calculate kinetic energy with mass {{ mass }} kg and velocity {{ velocity }} m/s",
    "variables": [
        {"mass": 10, "velocity": 5, "answer": "KE = 125 J"},
        {"mass": 2, "velocity": 10, "answer": "KE = 100 J"}
    ],
    "marks": 3
}
```

## Keybindings

| Command | Windows/Linux | Mac |
|---------|---------------|-----|
| Preview Quiz | `Ctrl+Shift+P` | `Cmd+Shift+P` |
| Generate Quiz | `Ctrl+Shift+G` | `Cmd+Shift+G` |
| Validate Questions | `Ctrl+Shift+V` | `Cmd+Shift+V` |

## 📋 Requirements

### Essential Components
```bash
# 1. Setwise CLI (required)
pip install git+https://github.com/nipunbatra/setwise.git

# 2. LaTeX Distribution (choose one)
# Ubuntu/Debian:
sudo apt-get install texlive-full

# macOS:
brew install --cask mactex

# Windows: Download from https://miktex.org/

# 3. Python 3.8+ (check version)
python3 --version
```

### Verification
```bash
# Test installation
setwise --help                    # Should show Setwise commands
pdflatex --version                # Should show LaTeX version
python3 -c "import jinja2"        # Should import without error
```

### Optional Enhancements
```bash
# For enhanced web interface
pip install git+https://github.com/nipunbatra/setwise.git[web]

# For development features
pip install git+https://github.com/nipunbatra/setwise.git[dev]
```

## Extension Settings

This extension contributes the following settings:

- `setwise.autoPreview`: Automatically preview quiz when questions file is opened
- `setwise.autoValidate`: Automatically validate questions on file save  
- `setwise.defaultTemplate`: Default template for quiz generation
- `setwise.autoFixLatex`: Automatically fix common LaTeX errors on save
- `setwise.previewSets`: Number of quiz sets to generate for preview

## ⚠️ Known Issues & Solutions

### Performance
- **Large files (>1000 questions):** May take 10-30 seconds to validate
  - *Solution:* Disable `autoValidate` for large files, validate manually
- **Live preview mode:** Resource intensive with complex LaTeX
  - *Solution:* Use manual preview (`Ctrl+Shift+P`) instead

### LaTeX Compilation
- **"pdflatex not found":** LaTeX not properly installed
  - *Solution:* Install full LaTeX distribution, restart VSCode
- **Complex math expressions:** May fail compilation
  - *Solution:* Use "Setwise: Fix LaTeX Errors" command

### Path Issues
- **"Setwise command not found":** CLI not in PATH
  - *Solution:* Reinstall with `pip install --user` or add to PATH
- **Preview not working:** PDF viewer issues
  - *Solution:* Enable VSCode PDF preview extension

### Template Variables
- **Variable rendering errors:** Undefined variables in templates
  - *Solution:* Use "Setwise: Validate Templates" to check consistency
- **Jinja2 syntax errors:** Invalid template expressions
  - *Solution:* Check template syntax with `{{ variable }}` format

## 📅 Release Notes

### 2.0.0 - Major Update! 🎉
- **🆕 v2.0 Template Support:** Full support for templated MCQ questions with variables
- **📋 Quiz Metadata:** Professional headers with title, duration, instructions
- **🧩 Enhanced Multi-Part Questions:** Individual marks and better structure
- **🎨 Improved Snippets:** New templates for v2.0 features
- **📊 Advanced Statistics:** Template usage tracking and validation insights
- **🔧 Better LaTeX Intelligence:** Enhanced error detection and fixing
- **⚡ Performance Improvements:** Faster validation and preview generation

### 1.2.0
- Added live preview mode with auto-refresh
- Enhanced LaTeX error detection and user-friendly messages
- New subject-specific snippet templates (Physics, Chemistry, Math)
- Improved IntelliSense with better auto-completion
- Added configurable output directories

### 1.1.0
- Multi-template support (default, compact, minimal)
- Chemical formula auto-conversion (H2O → H$_2$O)
- Interactive LaTeX help system
- File statistics display in status bar
- Improved syntax highlighting for complex LaTeX expressions

### 1.0.0 - Initial Release
- Core question editing with syntax highlighting
- One-click PDF preview and generation
- LaTeX validation and auto-fixing
- Comprehensive snippet library
- Real-time error detection

## 🤝 Support & Community

### Get Help
- 🐛 **Report Issues:** [GitHub Issues](https://github.com/nipunbatra/setwise-vscode-extension/issues)
- 💬 **Discussions:** [GitHub Discussions](https://github.com/nipunbatra/setwise/discussions)
- 📖 **Documentation:** [Setwise Documentation](https://nipunbatra.github.io/setwise)
- 📧 **Email Support:** setwise-support@example.com

### Contributing
```bash
# Clone and setup development environment
git clone https://github.com/nipunbatra/setwise-vscode-extension.git
cd setwise-vscode-extension
npm install

# Open in VSCode and press F5 to launch extension development host
```

### Useful Links
- 🏠 **Main Project:** [Setwise Quiz Generator](https://github.com/nipunbatra/setwise)
- 🌐 **Web Interface:** [Setwise Web](https://github.com/nipunbatra/setwise-web)
- 🎓 **Examples:** [Question Libraries](https://github.com/nipunbatra/setwise/tree/main/examples)
- 📚 **LaTeX Guide:** [Writing Questions](https://nipunbatra.github.io/setwise/question-format.html)

### Star the Project! ⭐
If you find this extension helpful, please star the [main repository](https://github.com/nipunbatra/setwise) and [extension repository](https://github.com/nipunbatra/setwise-vscode-extension)!

## 📄 License

**MIT License** - Free for educational and commercial use.

See [LICENSE](LICENSE) file for full details.

---

<div align="center">

**Transform VSCode into the ultimate quiz authoring environment!**

[⬇️ Install Extension](https://marketplace.visualstudio.com/items?itemName=setwise.setwise-questions) • [📖 Read Docs](https://nipunbatra.github.io/setwise) • [⭐ Star on GitHub](https://github.com/nipunbatra/setwise)

*Made with ❤️ for educators worldwide*

</div>