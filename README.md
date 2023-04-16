# jtrace

Refer to[JNI-Frida-Hook](https://github.com/Areizen/JNI-Frida-Hook)

Add more detailed jni information printing, with the main purpose of assisting unidbg to supplement the environment

**Complete**

# Prepare

```bash
pip install frida==14.2.18
pip install frida-tools==9.2.4
pip install objection==1.11.0
pip install hexdump
npm install
```

# Use

```bash
frida -U -n com.xingin.xhs -l _agent.js -o jni.log
frida -U -f com.xingin.xhs -l _agent.js -o jni.log --no-pause
frida -U -f com.iqiyi.i18n -l _agent.js -o jni.log --no-pause
frida -U -f com.cmcc.cmvideo.miguc -l _agent.js -o jni.log --no-pause
```

Due to different systems and frida versions embodying different systems, there are two versions

- `_agent.js` Faster, but may not be supported in some environments
    - Compile command `npm run build`
- `_agent_stable.js` 兼容性更好
    - Compile command `npm run build-stable`

There is no difference in the core key code, the main difference is that the stable version puts some calls in `Java.perform`

Tips! The script is being improved, please adjust the script yourself

# Features

- The log matches unidbg, and the environmental efficiency is improved
- Friendly to attach mode
- Easy to read code

# Illustrate

- `show_cache_log` Used to decide whether to print the information of the following jni methods
    - `GetFieldID`
    - `GetStaticFieldID`
    - `GetMethodID`
    - `GetStaticMethodID`
