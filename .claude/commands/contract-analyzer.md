---
model: sonnet
---

# Contract Analyzer Bot

## Purpose
Analyzes contracts, terms of service, and legal documents for dangerous, invasive, and unreasonable clauses before signing.

---

## Features

### 1. Document Support
- **PDF files** (.pdf)
- **Word documents** (.docx)
- **Text files** (.txt)
- **Web pages** (URLs)

### 2. Analysis Modes

#### Basic Mode (No API Key Required)
- Keyword-based pattern matching
- Works completely offline
- Fast analysis
- More false positives

#### AI Mode (Claude API)
- Intelligent context-aware analysis
- Fewer false positives
- Explains findings clearly
- Requires API key (~$0.01 per document)

### 3. Issue Detection

#### Dangerous Terms
- Unlimited liability waivers
- Broad indemnification clauses
- "Hold harmless" agreements
- Risk assumption clauses
- Legal rights waivers
- Consumer protection waivers

#### Invasive Terms
- Excessive data collection
- Third-party data sharing
- Tracking and monitoring
- Lack of data control
- Broad privacy waivers

#### Unreasonable Terms
- Automatic renewal without notice
- One-sided modification rights
- Unfair termination clauses
- No refund policies
- Forced arbitration clauses
- Class action waivers
- Jury trial waivers

### 4. Severity Ratings
- 🔴 **HIGH** - Consult a lawyer before signing
- 🟡 **MEDIUM** - Review carefully, consider negotiating
- 🔵 **LOW** - Minor concerns, read the details

---

## Location
`/Users/jennicastiehl/bots/contract-analyzer`

---

## Usage

### Analyze Local Files
```bash
cd /Users/jennicastiehl/bots/contract-analyzer

# PDF
./analyze ~/Documents/lease.pdf

# Word document
./analyze ~/Downloads/employment_contract.docx

# Text file
./analyze ~/Desktop/terms.txt
```

### Analyze Web Pages
```bash
# Terms of service
./analyze https://policies.google.com/terms

# Privacy policy
./analyze https://www.facebook.com/legal/terms

# Any webpage with legal text
./analyze https://stripe.com/legal/ssa
```

### JSON Output (for automation)
```bash
./analyze contract.pdf --json > results.json
```

### With Claude AI (better accuracy)
```bash
# Option 1: Pass API key as argument
./analyze contract.pdf --api-key YOUR_API_KEY

# Option 2: Set in config.yaml
# Edit config.yaml and add:
#   claude_api_key: "sk-ant-api03-..."
./analyze contract.pdf
```

---

## Example Output

```
================================================================================
CONTRACT ANALYSIS REPORT
Document: apartment_lease.pdf
================================================================================

SUMMARY:
  HIGH severity issues: 2
  MEDIUM severity issues: 5
  LOW severity issues: 1
  Total concerns: 8

HIGH SEVERITY ISSUES:
--------------------------------------------------------------------------------

[HIGH-1] LIABILITY
  Location: Section 12.3
  Concern: Unlimited indemnification clause
  Clause excerpt:
    Tenant agrees to indemnify and hold harmless Landlord from any and
    all claims, damages, losses, and expenses...

[HIGH-2] ARBITRATION
  Location: Section 18
  Concern: Forced arbitration with class action waiver
  Clause excerpt:
    All disputes shall be resolved through binding arbitration. Tenant
    waives right to participate in class action lawsuits...

================================================================================
RECOMMENDATION:
⚠️  HIGH RISK: Consult a lawyer before signing this document.
================================================================================
```

---

## Configuration

Edit `config.yaml` for API key:

```yaml
# Claude API key (optional, for AI-powered analysis)
claude_api_key: "sk-ant-api03-..."

# Analysis settings
analysis:
  mode: "auto"  # auto, basic, ai
  severity_threshold: "low"  # low, medium, high
```

---

## Common Use Cases

### Personal Contracts
- 📄 Apartment/house leases
- 💼 Employment contracts & NDAs
- 🏥 Medical consent forms
- 🎓 School enrollment agreements
- 🎯 Freelance/contractor agreements

### Online Services
- 💻 Software licenses & Terms of Service
- 🛒 E-commerce purchase agreements
- 💳 Financial services agreements
- 📱 App privacy policies
- 🎮 Gaming platform terms

### Business Contracts
- 🏢 Vendor/supplier contracts
- 🤝 Partnership agreements
- 📊 Service level agreements (SLAs)
- 🔒 Data processing agreements

---

## Technical Details

### Document Processing
- **PDF**: PyPDF2 for text extraction
- **DOCX**: python-docx for Word documents
- **Web**: BeautifulSoup + requests for HTML scraping
- **Text**: Direct file reading

### Pattern Matching (Basic Mode)
Keyword categories:
```python
DANGEROUS_KEYWORDS = [
    "indemnify", "hold harmless", "waive liability",
    "at your own risk", "assume all risk", ...
]

INVASIVE_KEYWORDS = [
    "collect personal information", "share with third parties",
    "track your activity", "monitor usage", ...
]

UNREASONABLE_KEYWORDS = [
    "automatically renew", "modify terms without notice",
    "binding arbitration", "class action waiver", ...
]
```

### AI Analysis (Claude Mode)
- Uses Claude 3.5 Sonnet for analysis
- Provides context-aware explanations
- Identifies clause locations
- Offers actionable recommendations

---

## Files

```
contract-analyzer/
├── analyzer.py           # Main analysis engine
├── analyze               # Command-line wrapper (symlink)
├── config.yaml          # Configuration (gitignored)
├── config.example.yaml  # Configuration template
├── test_contract.txt    # Sample contract for testing
├── requirements.txt     # Python dependencies
├── README.md           # Documentation
└── QUICKSTART.md       # Quick start guide
```

---

## Installation

```bash
cd /Users/jennicastiehl/bots/contract-analyzer

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Make executable
chmod +x analyze analyzer.py
```

---

## API Key Setup (Optional)

### Get Claude API Key
1. Go to https://console.anthropic.com/
2. Sign up or log in
3. Navigate to API Keys
4. Create a new key
5. Add to `config.yaml`

### Cost
- ~$0.01 per document
- Claude Sonnet 3.5 pricing: ~$3 per million tokens
- Average contract: ~3,000 tokens

---

## Limitations

### What This Bot Cannot Do
- ❌ Cannot provide legal advice
- ❌ May miss context-dependent issues
- ❌ Basic mode has more false positives
- ❌ Best with English documents
- ❌ Cannot interpret complex legalese perfectly

### What You Should Still Do
- ✅ Read the full document yourself
- ✅ Consult a lawyer for important contracts
- ✅ Review HIGH severity items carefully
- ✅ Ask for modifications (many terms are negotiable)

---

## Privacy & Security

### Basic Mode
- ✅ 100% offline analysis
- ✅ Documents never leave your machine
- ✅ No data sent anywhere
- ✅ Complete privacy

### AI Mode (with API key)
- ⚠️ Document text sent to Claude API
- ✅ Anthropic does not store or train on your data
- ✅ Encrypted transmission (HTTPS)
- ⚠️ See Anthropic's privacy policy for details

### Best Practices
- ❌ Do NOT commit config.yaml with API key
- ❌ Do NOT share sensitive contracts in public repos
- ✅ Use basic mode for highly sensitive documents
- ✅ Review Claude's data usage policy

---

## Real-World Examples

### Banking Agreement (Chase)
```bash
./analyze https://static.chasecdn.com/content/dam/legal-agreements/library/en/dsa_la/versions/dsa_la.pdf
```
**Result**: MEDIUM risk - Binding arbitration clause (industry standard)

### Google Terms of Service
```bash
./analyze https://policies.google.com/terms
```
**Result**: LOW risk - Standard tech company ToS

### Apartment Lease
```bash
./analyze ~/Documents/lease.pdf
```
**Result**: HIGH risk - Unlimited liability, unfair termination

---

## Tips

1. **Always read the full document** - This tool highlights problem areas
2. **Focus on HIGH severity** - These are most important
3. **Many terms are negotiable** - Ask for changes!
4. **When in doubt, ask a lawyer** - Especially for employment, real estate
5. **Check for opt-out periods** - Arbitration clauses often allow opt-out within 30-60 days

---

## Support

For issues:
1. Test with sample contract: `./analyze test_contract.txt`
2. Check document format compatibility
3. Verify API key if using AI mode
4. Review analyzer.log for errors
