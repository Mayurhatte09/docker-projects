
---

#  Step-by-Step: Working Through Docker Lab Repo

##  1: Clone & Open the Project

Run this in your terminal:

```bash
git clone https://github.com/Mayurhatte09/docker-projects-lab.git
cd docker-projects-lab
```

Then open it in:

* VS Code (recommended)

---

##  2: Understand the Structure

Inside the repo, look for:

* `Dockerfile` → how the image is built
* `docker-compose.yml` → multi-container setup
* Project folders (like `app/`, `nginx/`, etc.)

 Before running anything, **read the Dockerfile once**.
You’re looking for:

* Base image (`FROM`)
* Dependencies (`RUN`)
* App copy (`COPY`)
* Start command (`CMD`)

---

##   3: Run Your First Container

### If there’s a Dockerfile:

```bash
docker build -t my-first-app .
docker run -p 8080:8080 my-first-app
```

 Then open:

```
http://localhost:8080
```

---

##  4: If You See docker-compose.yml

Run:

```bash
docker-compose up -d
```

Check running containers:

```bash
docker ps
```

Stop everything:

```bash
docker-compose down
```

---

##  5: Understand What Just Happened

When you ran it:

* Docker created an **image**
* Then started a **container**
* If compose:

  * Multiple services talked to each other (like app + DB)

---

##  6: Modify Something (IMPORTANT)

This is where real learning happens.

Try ONE of these:

###  Change port

In:

* `Dockerfile` or `docker-compose.yml`

Change:

```yaml
ports:
  - "8080:8080"
```

to:

```yaml
  - "5000:8080"
```

---

###  Break & fix

* Delete a line in Dockerfile
* Rebuild → see error
* Fix it

This builds debugging skills (very valuable)

---

##  7: Inspect Containers

Run:

```bash
docker exec -it <container_id> bash
```

Now you're **inside the container** 

Check:

```bash
ls
env
```

---

##   8: Check Logs

```bash
docker logs <container_id>
```

This helps when:

* App doesn’t start
* Port not working
* Errors happen

---

##  What You Should Aim to Learn

By the end of this repo, you should clearly understand:

* Difference between **image vs container**
* How a **Dockerfile works**
* How **multi-container apps** run
* Basic debugging

