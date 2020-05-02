# Kubernetes resources limits - Rabbit Hole

**Q: Which resources can I limit?**
- CPU
- Memory
- Linux Huge Pages 

[[source](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-types)]

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

Q: What's the difference between requests and limits?


**Q: Is the limit configured per pod or per container?**
- Per container.

**Q: What happens if the limit is exceeded?**
- cpu limit - the container is throttled, will not get more CPU time
- memory limit - the container will be killed

**Q: How Kubernetes implements resources limits?**
- K8s passes them to docker (or other container engine)

Q: How can one check what values were passed to docker? Is there docker run command logged somewhere?

Q: How docker implements resources limits?

Q: What are the consequences of not specifying CPU and Memory limits at all?


---------------------------------
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>
