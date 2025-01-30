## 🚀 Ansible Playbook: Execute Git Commands in Subdirectories

### 📌 Overview
This Ansible playbook iterates through subdirectories (non-recursively) within a specified parent directory and executes a Git command (e.g., git pull) in each subdirectory.

### ✨ Features
✅ Lists all direct subdirectories of the specified dir_path.  
✅ Executes the given Git command inside each subdirectory.  
✅ Uses variables from an external file for flexibility. 

### 📋 Requirements
🔹 Ansible installed on the system.  
🔹 Git installed and configured.  
🔹 The specified dir_path should exist and contain Git repositories.

### ⚙️ Variables (vars/default_vars.yml)
| 🔧 Variable   | 📖 Description                                          | 🏷 Default Value |
|--------------|---------------------------------------------------------|-----------------|
| `dir_path`   | Parent directory containing subdirectories with Git repositories. | `~/konnect`     |
| `git_command` | Git command to execute inside each subdirectory.       | `git pull`      |

### 🛠 How It Works
1️⃣ The playbook first finds all immediate subdirectories inside dir_path.  
2️⃣ It stores these subdirectories in the dirs variable.  
3️⃣ It executes the given Git command (git pull by default) inside each subdirectory.  

### ▶️ Usage
#### 🔹 1. Clone the Repository (if applicable)
```bash
  git clone <repo-url>
  cd <repo-directory>
```
#### 🔹 2. Modify Variables (Optional)
Edit vars/default_vars.yml to set your preferred directory and Git command.

#### 🔹 3. Run the Playbook
```bash
ansible-playbook playbook.yml
```
### 🖥 Example Output
```yaml
PLAY [iterates through subdirectories in non-recursive manner and execute git command] ****************

TASK [list all directories in mentioned parent directory] *********************************************
ok: [localhost]

TASK [execute git command] ****************************************************************************
changed: [localhost] => (item=/home/user/konnect/repo1)
changed: [localhost] => (item=/home/user/konnect/repo2)

PLAY RECAP ********************************************************************************************
localhost: ok=3 changed=1 failed=0
```
### 📌 Notes
⚠️ The playbook does not recurse into nested subdirectories.  
⚠️ Ensure that each subdirectory is a valid Git repository.  
⚙️ The Git command can be changed to other commands like git status or git fetch in vars/default_vars.yml.  

### 📜 License
📝 This project is licensed under the MIT License.
