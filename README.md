# Notes
Notes For Quick Reminders

# Table of Content
1. [Vite](#Vite)
2. [Markdown](#Markdown)
3. [Ports](#Ports)

<!-----------------------------------------------------  -->

# <a name="Vite">1. Vite</a>

<details>
<Summary>How to Setup with VITE</Summary>


```bash
    npm create vite@latest
```
- Follow on screen instructions. 
- If you already created a folder for project, leave project name empty. 
- Select what you need from displayed list.

</details>

<!-- ---------------------------------------------------- -->

# <a name="Markdown">2. Markdown</a>

<details>
<Summary>Table of Contents Link</Summary>
 
```bash
[placeholder](#MyTitle)
```
```bash
<a name="MyTitle">MyTitle</a>
```

</details>
<!-- ---------------------------------------------------- -->

# <a name="Ports">3. Ports</a>

<details>
<Summary>Port List and Kill a Specific Port Process</Summary>
 
```bash
netstat -ano | findstr :<port_number>
OUTPUT: TCP    0.0.0.0:<port_number>       0.0.0.0:0              LISTENING       <PID>
```
```bash
taskkill /PID <PID> /F
```

</details>