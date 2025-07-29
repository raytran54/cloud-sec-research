# AWS Security Tools Collection

A comprehensive guide to essential AWS security and reconnaissance tools for cloud security professionals and penetration testers.

## 🔧 Tools Overview

This repository provides setup and usage instructions for three powerful AWS security tools:

- **CloudList** - Multi-cloud asset discovery and enumeration
- **CloudMapper** - AWS infrastructure visualization and security analysis
- **Pacu** - AWS penetration testing framework

## 🌩️ CloudList

CloudList is a multi-cloud enumeration tool that helps discover and list assets across various cloud providers including AWS, Azure, GCP, and more.

### Installation

1. **Install CloudList**
   ```bash
   go install github.com/projectdiscovery/cloudlist/cmd/cloudlist@latest
   ```

2. **Add to PATH**
   Add this line to your `~/.zshrc`:
   ```bash
   export PATH="$HOME/go/bin:$PATH"
   ```

3. **Reload shell configuration**
   ```bash
   source ~/.zshrc
   ```

4. **Verify installation**
   ```bash
   cloudlist -h
   ```

### Usage

**AWS Configuration:**
```bash
export AWS_ACCESS_KEY_ID="YOUR_AWS_ACCESS_KEY"
export AWS_SECRET_ACCESS_KEY="YOUR_AWS_SECRET_KEY"
export AWS_REGION="us-east-1"
```

**Run CloudList:**
```bash
cloudlist -provider aws
```

## 🗺️ CloudMapper

CloudMapper provides network visualization and security analysis for AWS environments, generating interactive maps and security reports.

### Installation

1. **Clone repository**
   ```bash
   git clone https://github.com/duo-labs/cloudmapper.git
   cd cloudmapper/
   ```

2. **Install dependencies**
   ```bash
   brew install autoconf automake awscli freetype jq libtool python3
   ```

3. **Setup Python environment**
   ```bash
   python3 -m venv ./venv && source venv/bin/activate
   pip install --prefer-binary -r requirements.txt
   ```

### Usage

1. **Prepare network data**
   ```bash
   python cloudmapper.py prepare --config config.json.demo --account demo(tên định nghĩa lấy từ file config)
   ```

2. **Generate security report**
   ```bash
   python cloudmapper.py report --config config.json.demo --account demo(tên định nghĩa lấy từ file config)
   ```

3. **Start web server**
   ```bash
   python cloudmapper.py webserver
   ```

4. **Access results**
   - Network map: http://127.0.0.1:8000/
   - Security report: http://127.0.0.1:8000/account-data/report.html

## 🔍 Pacu

Pacu is an open-source AWS penetration testing framework designed for offensive security testing of AWS environments.

### Installation

1. **Clone repository**
   ```bash
   git clone https://github.com/RhinoSecurityLabs/pacu.git
   cd pacu
   ```

2. **Setup Python environment**
   ```bash
   python3 -m venv ./venv && source venv/bin/activate
   pip install -r requirements.txt
   ```

### Usage

1. **Start Pacu**
   ```bash
   python3 cli.py
   ```

2. **Configure AWS credentials**
   ```
   set keys
   ```

3. **Run specific modules**
   ```
   run <module_name>
   ```

## 📊 Tool Comparison

| Feature | CloudList | CloudMapper | Pacu |
|---------|-----------|-------------|------|
| **Primary Purpose** | Asset Discovery | Visualization & Analysis | Penetration Testing |
| **Target Audience** | Security Teams, DevOps | Cloud Architects, Security Analysts | Penetration Testers, Red Teams |
| **Learning Curve** | Low | Medium | High |
| **Multi-Cloud Support** | ✅ Excellent | ❌ AWS Only | ❌ AWS Only |
| **Visualization** | ❌ None | ✅ Excellent | ❌ Limited |
| **Automation** | ✅ High | ✅ Medium | ✅ High |
| **Reporting** | ❌ Basic | ✅ Comprehensive | ✅ Detailed |

### Advantages & Disadvantages

#### CloudList
**✅ Pros:**
- Fast and lightweight
- Multi-cloud provider support
- Easy integration with other tools
- Minimal resource requirements
- Simple command-line interface

**❌ Cons:**
- Limited detailed analysis
- No visualization capabilities
- Basic reporting functionality
- Requires additional tools for deep analysis

#### CloudMapper
**✅ Pros:**
- Excellent network visualization
- Comprehensive security reports
- User-friendly web interface
- Good for compliance auditing
- Detailed infrastructure mapping

**❌ Cons:**
- AWS-only support
- Resource intensive
- Complex setup process
- Limited real-time capabilities
- Requires significant storage for large environments

#### Pacu
**✅ Pros:**
- Comprehensive penetration testing modules
- Active development and community
- Modular architecture
- Detailed exploitation capabilities
- Extensive AWS service coverage

**❌ Cons:**
- Steep learning curve
- Potential for destructive actions
- Requires deep AWS knowledge
- Limited to AWS environments
- May trigger security alerts

## 🎯 Use Case Recommendations

- **Asset Discovery**: Use **CloudList** for quick enumeration across multiple cloud providers
- **Infrastructure Analysis**: Use **CloudMapper** for comprehensive AWS environment visualization
- **Security Testing**: Use **Pacu** for thorough penetration testing and vulnerability assessment
- **Combined Approach**: Use all three tools together for complete cloud security assessment

## ⚠️ Security Considerations

- Always obtain proper authorization before using these tools
- Use dedicated test environments when possible
- Monitor AWS CloudTrail logs for unusual activity
- Follow responsible disclosure practices
- Ensure compliance with organizational security policies

## 📝 License

Please refer to each tool's respective repository for licensing information:
- [CloudList License](https://github.com/projectdiscovery/cloudlist)
- [CloudMapper License](https://github.com/duo-labs/cloudmapper)
- [Pacu License](https://github.com/RhinoSecurityLabs/pacu)

## 🤝 Contributing

Contributions to improve this guide are welcome! Please submit pull requests or open issues for suggestions.

---

**Disclaimer**: These tools should only be used on systems you own or have explicit permission to test. Unauthorized use may violate laws and regulations.
