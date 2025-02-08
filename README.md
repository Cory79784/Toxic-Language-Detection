Overview
**This project investigates toxic language detection on Stormfront.org, a far-right extremist forum. We compare two approaches:

1. Machine Learning using the HateScan API
2. Custom Dictionary-based detection

**Key Findings
                       Performance Comparison
Method	              Krippendorff’s Alpha	                Strengths	Limitations
Machine Learning	       0.791 (Moderate)            Detects overt toxicity effectively	Struggles with nuanced/coded language
Dictionary-based	       0.607 (Low)	               Fast keyword matching	Fails to capture contextual meaning

**Toxic Language Patterns
Primary Targets:
1.Racial groups (Black, Asian, Middle Eastern)
2.Religious groups (Jews, Muslims)
3.Immigrants and feminists


**Common Tactics:
1.Dehumanization ("subhuman", "vermin")
2.Conspiracy theories ("Jewish control")
3.Demographic fearmongering ("breeding threat")


*Dataset
Source: 5,000 comments from Stormfront.org


*Processing:
1. Removed metadata
2. Balanced sampling (191 toxic/355 non-toxic for ML)
3. Multi-stage dictionary refinement


*Methodology
1. Machine Learning Pipeline

graph TD
A[Raw Comments] --> B[HateScan API]
           B    --> C{Toxicity Threshold}
           C    -->|≥50%| D[Toxic]
           C    -->|<50%| E[Non-toxic]

2. Dictionary Approach

Development Process:
1.Initial 600-term seed from ChatGPT
2.Iterative refinement cycles
3.Contextual filtering (e.g., negation handling)
4.Final dictionary: 3,983 flagged terms


**Reproducibility
Implementation Steps
1.Data preprocessing:
def clean_text(text):
    return re.sub(r'[^\w\s]', '', text).lower()
    
2.Machine learning analysis:
hatescan = HateScanAPI(api_key='YOUR_KEY')
results = [hatescan.predict(comment) for comment in corpus]

3.Dictionary implementation:
python dictionary_scanner.py --input comments.csv --output flagged.csv


**Ethical Considerations
1. Annotator mental health protocols
2. Secure data handling procedures
3. Bias mitigation through multi-perspective review
4. Limited data sharing to prevent hate speech propagation
