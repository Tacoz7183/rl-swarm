# Gensyn AI Node Setup on 32-Core CPU (Linux)

This guide explains how to set up and run a Gensyn AI node using a 32-core CPU on a Linux-based system.

---

## System Requirements

- **CPU**: 32-core (x86_64 or ARM64)
- **RAM**: 16+ GB (20+ GB recommended)
- **Storage**: 200 GB SSD minimum
- **OS**: Ubuntu 20.04 or 22.04
- **Python**: 3.10 or higher
- **Network**: 100 Mbps or faster

---

## Installation Steps

### 1. Update System
```bash
sudo apt update -y && sudo apt upgrade -y
```

### 2. Install Dependencies
```bash
sudo apt install -y python3 python3-venv python3-pip curl git screen nodejs npm
```

Install Yarn:
```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install -y yarn
```

### 3. Clone RL-Swarm Repository
```bash
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm
```

### 4. Setup Python Environment
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 5. Install Python Dependencies
```bash
pip install --upgrade pip
pip install -r requirements-cpu.txt
```

### 6. Install JS Dependencies
```bash
cd modal-login
yarn install
yarn upgrade
yarn add next@latest viem@latest
cd ..
```

### 7. Run the Gensyn Node
```bash
./run_rl_swarm.sh
```

---

## Runtime Prompts

- **Connect to Testnet**: Enter `Y`
- **Swarm Type**: `A` for Math, `B` for Math Hard
- **Model Size**: Choose from 0.5, 1.5, 7, 32, or 72 billion

Youâll log in at [localhost:3000](http://localhost:3000/) and get your `ORG_ID`.

---

## Model Size & RAM Recommendations

| Model | RAM Needed |
|-------|------------|
| 0.5B  | 4 GB       |
| 1.5B  | 8 GB       |
| 7B    | 16 GB      |
| 32B   | 50 GB      |
| 72B   | 100 GB     |

---

## Resources

- [Official RL-Swarm Repo](https://github.com/gensyn-ai/rl-swarm)
- [Gensyn Node Setup Video](https://www.youtube.com/watch?v=IGHcCqij8qU)

---

## License

This guide is provided under the MIT License.