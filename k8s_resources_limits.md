# Kubernetes resources limits

**Q: Which resources can I limit?**
- CPU, Memory and Linux Huge Pages [[source](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-types)]

**Q: How can I limit them?**
```
...
spec:
  containers:
  - name: db
    ...
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m"
      limits:
        memory: "128Mi"
        cpu: "500m"
```

**Q: Is the limit configured per pod or per container?**
- Per container.

**Q: What happens if the limit is exceeded?**

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>
