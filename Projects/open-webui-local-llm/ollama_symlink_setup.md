# 🧠 Offloading Ollama Model Storage to External SSD

To conserve internal disk space on my Mac mini, I redirected Ollama's model storage (`~/.ollama/models`) to an external Thunderbolt 4 SSD using a symbolic link. This allows large language model blobs (often several GBs each) to be stored externally while keeping Ollama fully operational.

---

## Hardware:
Machine: Mac Mini 24G+256G
m.2 SSD: ZhiTai TiPlus7100 2TB  
SSD Enclosure: ITGZ USB4 enclosure

## 📁 Target Path
External SSD name: `iTGZ_2t`  
Destination folder for model storage: `/Volumes/iTGZ_2t/AI_lib/models`

---

## 🔧 Step-by-Step Setup

### 1. Move existing models to external disk

```bash
mv ~/.ollama/models /Volumes/iTGZ_2t/AI_lib/models
```

> ⚠️ Make sure Ollama is not running when doing this step.

---

### 2. Create symbolic link pointing to external disk

Then I created a symbolic link so that Ollama still “thinks” the models are in the default path:

```bash
ln -s /Volumes/iTGZ_2t/AI_lib/models ~/.ollama/models
```

Resulting output from `ls -l ~/.ollama`:

```bash
lrwxr-xr-x  1 caydeli  staff  31  8 May 23:13 /Users/caydeli/.ollama/models -> /Volumes/iTGZ_2t/AI_lib/models
```

---

## ✅ Result

- Ollama continues to operate as normal.
- Large model files (blobs) are now hosted on the external SSD.
- Internal disk space usage dropped significantly (~50GB freed after cleanup).

---

## 🧼 (Optional) Delete old hidden local blobs (if duplicated)

Even after linking, you might need to manually remove hidden or duplicated model files under `.ollama` if they weren't moved cleanly:

```bash
du -sh ~/.ollama/*
```

Then confirm model paths are clear and only symbolic link remains.

---

## 📌 Notes

- Always ensure the external SSD (`iTGZ_2t`) is mounted before running Ollama or Open WebUI.
- If the SSD is missing, Ollama may fail to start or re-download models.
