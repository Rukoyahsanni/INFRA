# 🛠️ Troubleshooting Guide

This guide documents known issues encountered during the setup and deployment of the **Terraform-Jenkins-AWS Infrastructure Project**, along with their resolutions.

---

## ❗ Issue: `Command line option '[from -y]' is not understood`

### Description

When provisioning the EC2 instance and using `remote-exec` to run `install_jenkins.sh`, the following error appeared:

E: Command line option '[from -y]' is not understood in combination with the other options.
install_jenkins.sh: line 9: $'\r': command not found


---

### 💡 Root Cause

- The shell script had **Windows-style (CRLF)** line endings.
- Linux interprets `\r` as part of the command, which causes unexpected parsing issues.

---

### ✅ Solution

Convert the script from CRLF to LF before applying the Terraform configuration.

#### Option 1: Convert in Visual Studio Code
- Open the file in VS Code.
- Click on the line ending type at the bottom right (usually shows `CRLF`).
- Select `LF`.

#### Option 2: Convert via Terminal

Install `dos2unix` (if not installed):
```bash
sudo apt-get install dos2unix
```
Then run:
```bash
dos2unix install_jenkins.sh
```
Re-run your Terraform deployment:
```bash
terraform apply
```

✅ Outcome
After converting the line endings, the script executed without errors, Jenkins installed successfully, and the pipeline was able to run.

Tip: Always ensure that any shell scripts you use with remote-exec are in LF format to avoid issues on Linux-based EC2 instances.

