# Windows: PowerShell

```
Error: Could not find or load main class .etrap.medusa.config.ClassConfig=conf.tracer_config.xml
```

**Cause**: Windows PowerShell seems to misinterpret the class due to the `-` in the command. In other words, it looks for `.etrap.medusa.config.ClassConfig=conf.tracer_config.xml` instead of `-Deu.etrap.medusa.config.ClassConfig=conf/tracer_config.xml`

**Solution**: Do not use the PowerShell but switch to the Command Line.

