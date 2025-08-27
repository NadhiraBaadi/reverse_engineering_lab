# reverse_engineering_lab
A hands-on Reverse Engineering lab with tools, cheat sheets, challenges, and a 3-month learning roadmap. Includes CTF practice tasks, debugging guides, and curated resources for beginners to advanced learners.


Welcome to the **Reverse Engineering Lab** — a structured, hands-on space to learn and practice **reverse engineering, debugging, binary exploitation, and CTF challenges**.  

This repo is designed for **learners, teams, and educators** who want a step-by-step path into RE, with tools, challenges, and resources all in one place.  


##  Repository Structure
reverse_engineering_lab/
│── README.md # Overview (this file)

│── LICENSE # CC BY-NC 4.0 (educational use only)

│── .gitignore # Ignore binaries, logs, junk files

│
├── tools/ # Guides & cheat sheets for RE tools

│ ├── gdb/

│ │ ├── README.md # GDB basics + usage

│ │ └── examples/ # Practice C binaries

│ ├── radare2/README.md

│ ├── ghidra/README.md

│ ├── strace/README.md

│ └── objdump/README.md
│
├── roadmap/ # Learning roadmap

│ ├── month1_fundamentals.md

│ ├── month2_dynamic.md

│ ├── month3_advanced.md

│ └── phases.md # 90-day breakdown
│
├── challenges/ # Practice & CTF challenges

│ ├── month1/

│ ├── month2/

│ └── month3/
│
├── resources/ # Learning materials

│ ├── books.md

│ ├── websites.md

│ ├── youtube.md

│ └── courses.md
│
└── writeups/ # Solutions & team writeups

├── picoctf_2025/

├── crackmes_one/

└── internal_ctf/



##  Getting Started

### 1. Setup Environment
 Install **Linux VM** or **Windows VM**  
 Get essential tools:
 
   [Ghidra](https://ghidra-sre.org/)
   
   [IDA Free](https://hex-rays.com/ida-free/)
   
   [Radare2 / Cutter](https://rada.re/n/radare2.html)
   
   [x64dbg](https://x64dbg.com/)
   
   `strings`, `objdump`, `strace`, `ltrace`

### 2. Follow the Roadmap
Start from [roadmap/](./roadmap/) — a **3-month guided plan**:

  **Month 1:** Assembly & static analysis  
  
  **Month 2:** Debugging, unpacking, patching  
  
 🔥 **Month 3:** Anti-debug, malware, full CTFs  

### 3. Practice with Tools
Each tool has:
  Beginner-friendly guide  
  Example binaries  
  Exercises  

Check [tools/gdb/examples](./tools/gdb/examples/) for a quick start.

### 4. Solve Challenges
Go to [challenges/](./challenges/) and try **CrackMes, CTF puzzles, and team tasks**.  

### 5. Document Your Journey
 Write solutions in [writeups/](./writeups/).  
 Share knowledge with your team.  



##  Learning Resources

  **Books** → [resources/books.md](./resources/books.md)  
  **Websites** → [resources/websites.md](./resources/websites.md)  
  **YouTube Channels** → [resources/youtube.md](./resources/youtube.md)  
  **Courses** → [resources/courses.md](./resources/courses.md)  

Curated from the best in the RE community: LiveOverflow, Gynvael, John Hammond, RPISEC MBE, and more.  



##  Team CTF Mode

 Every **month ends with a CTF-style challenge** (see [roadmap](./roadmap/))  
 Solve as a team, then write your solution in [writeups/](./writeups/).  
 Suggested platforms:
   [crackmes.one](https://crackmes.one)  
   [reversing.kr](https://reversing.kr)  
   [picoctf.org](https://picoctf.org)  
   [root-me.org](https://root-me.org)  
   [ctftime.org](https://ctftime.org/task/)  



##  Contributing

 Fork the repo  
 Add your writeup, new challenge, or resource  
 Open a Pull Request  

 If you **learn from this repo or reuse its content**, please **mention this project and credit the author**.  
> It helps others discover it and keeps the lab growing 🌱.  



## 📜 License

This project is licensed under:  
**Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**  

You are free to:  
 ✅ Share — copy & redistribute for **educational purposes**  
 ✅ Adapt — remix, transform, build upon it  
 ❌ No commercial use  

📌 Please **credit [Your Name](https://github.com/yourusername)** when using material from this repo.  

Full license: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)



##  Motto

> **“Learn Deeply, Share Freely.”**  
Knowledge grows when passed on.  

