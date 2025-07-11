# Python Installation - Windows

## 1. Preparation

- Open PowerShell with administrative right
- If you use Win 32

  - `New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force`

- `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine`

## 2. Install `choco` and software

- `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`

- Close and reopen with administrative right
  - `choco install vscode -y`
  - `choco install git -y`
  - `choco install swig -y`

## 3. Install `uv` and Python

- Powershell with administrative right
  - `powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"`
- Close and reopen powershell (normal right)

  - `uv python install 3.12`

- Create virtual environment for normal usage (not for RL)
  - `uv venv --python 3.12`
  - `~/.venv/Scripts/activate.ps1`
  - `uv pip install jupyterlab ipykernel pandas matplotlib seaborn openpyxl ruff notebook xlsxwriter`

## 4. Install `Build Tools for Visual Studio 2022`

- Visit https://visualstudio.microsoft.com/downloads/?q=build+tools#build-tools-for-visual-studio-2022
- Install `Desktop development with C++` workload

## 5. Configure VSCode

- Install VSCode extensions
  - Python Extension Pack
  - Jupyter
  - Ruff
- Go to VSCode setting
  - `python.venvPath` -> `~`
  - `editor.formatOnSave` -> ✔️

## 6. Run RL codes

- Open powershell
  - `cd ~/Desktop`
  - `git clone https://github.com/warisa-cmu/rl-training-2025-codes.git`
  - Open VSCode and set workspace to the newly created folder
- Open VSCode terminal
  - `uv sync`
  - Try running the file in `src/T00_setup`
