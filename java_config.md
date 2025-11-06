---
title: Java
---

# Mac Java Installation Steps

1. **Download and Install Java**
2. **Check installed JDKs**

- `/usr/libexec/java_home -V` _[for Mac]_
- `java -version` _[for Windows]_

3. **Open `.zshrc` and set JAVA_HOME**

- `vi ~/.zshrc` _[using terminal]_
- `export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-17.jdk/Contents/Home` _[add this]_
- `esc → :wq` _[Save and exit]_

4. **Save and reload shell config in terminal**

- `source ~/.zshrc`

5. **Check Java HOME is setup properly from terminal**

- `echo $JAVA_HOME`

# Windows Java Installation Steps

1. **Download and Install Java**
2. **Check installed JDKs**

- `java -version` _[for Windows]_

3. **Set JAVA_HOME Environment Variable**

- Open **System Properties → Advanced → Environment Variables**
- Under **System variables**, click **New** and add:
  - **Variable name:** JAVA_HOME
  - **Variable value:** `C:\Program Files\Java\jdk-17` _[or your JDK path]_
- Click **OK** to save

4. **Update PATH Variable**

- In the same **Environment Variables** window, select **Path → Edit → New**, then add:
  - `%JAVA_HOME%\bin`
- Click **OK** to save and close

5. **Verify Configuration in Command Prompt**

- `java -version`
- `echo %JAVA_HOME%`

# Postman | Get Value from One API Response and Pass into Another API Request

[Watch Tutorial on YouTube](https://www.youtube.com/watch?v=5PM4gyE-ZWM)
