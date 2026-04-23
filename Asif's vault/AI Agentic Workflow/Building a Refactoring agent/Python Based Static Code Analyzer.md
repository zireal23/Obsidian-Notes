You are a senior software engineer. I want you to build a clean, extensible AST parsing module for a larger ingestion pipeline that will analyze large legacy Java codebases (including very large classes and methods).

Do NOT overcomplicate things, but DO follow good architecture and separation of concerns.

---

# 🎯 Goal

Build a Python-based AST parsing system that:

1. Parses Java files using a proper parser (JavaParser via subprocess, javalang, or tree-sitter — prefer tree-sitter if possible)
    
2. Traverses the AST using a visitor-like pattern
    
3. Extracts structured information about:
    
    - classes
        
    - methods
        
    - method calls
        
4. Produces clean, structured JSON-like output (Python dicts)
    

This is ONLY the AST + extraction layer. Do NOT implement:

- graph building
    
- chunking
    
- embeddings
    
- LLM logic
    

---

# 🧱 Requirements

## 1. Project Structure

Follow this modular structure:

ingestion/  
parser/  
parser.py  
visitor.py  
extractors/  
method_extractor.py  
call_extractor.py  
models/  
method_model.py  
class_model.py  
pipeline/  
parse_file.py

---

## 2. Data Models

Define clean Python classes or dataclasses for:

### MethodModel

- id (ClassName.methodName)
    
- class_name
    
- method_name
    
- parameters (list)
    
- return_type
    
- calls (list of method names)
    
- start_line
    
- end_line
    

### ClassModel

- class_name
    
- methods (list of MethodModel)
    

---

## 3. Parser Layer

Implement a parser that:

- takes a Java file as input
    
- builds an AST using tree-sitter (preferred) or javalang
    
- returns the root node
    

---

## 4. Visitor

Implement a visitor system that:

- walks the AST recursively
    
- maintains state:
    
    - current_class
        
    - current_method
        

---

## 5. Extractors

Implement separate extractor modules:

### MethodExtractor

- triggers on method declaration nodes
    
- creates MethodModel
    
- sets current_method
    

### CallExtractor

- triggers on method call nodes
    
- appends to current_method.calls
    

Keep extractors modular and loosely coupled.

---

## 6. Traversal Behavior

During AST traversal:

- When entering a class → set current_class
    
- When entering a method → create MethodModel and set current_method
    
- When encountering a method call → record it
    
- When exiting a method → finalize and store it
    

---

## 7. Output Format

The final output for a file should be:

{  
"file": "TradeProcessor.java",  
"classes": [  
{  
"class_name": "TradeProcessor",  
"methods": [  
{  
"id": "TradeProcessor.processTrade",  
"calls": ["validateTrade", "updatePosition"],  
"start_line": ...,  
"end_line": ...  
}  
]  
}  
]  
}

---

# ⚠️ Constraints

- Do NOT attempt full type resolution
    
- Do NOT try to resolve method calls across files
    
- Do NOT infer business logic
    
- Keep it deterministic and simple
    

---

# 🧪 Demonstration

Include a small example Java file and show:

- how the parser runs
    
- what output it produces
    

---

# 🧼 Code Quality

- Use clean, readable Python
    
- Add docstrings explaining each component
    
- Keep functions small and focused
    
- Avoid giant classes
    

---

# 🚀 Deliverable

Provide:

1. Full code for all modules
    
2. A simple runner script (parse_file.py)
    
3. Example input + output
    

---

Focus on clarity, extensibility, and correctness over completeness.
