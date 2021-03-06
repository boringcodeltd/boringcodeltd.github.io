# Kubernetes resources limits - Down the Rabbit Hole

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
- `kubectl get resourcequota your_pod --output=yaml` [source](
- Kubernetes uses Docker Api via docker.sock, not `docker run` command. [Api doc](https://docs.docker.com/engine/api/v1.24/)

Q: How docker implements resources limits?
- by modifing cgroups

Q: What's cgroup?
- Control Group - Linux kernel feature. [man](http://man7.org/linux/man-pages/man7/cgroups.7.html)

Q: How cgroup implements resources limits?
- Cpu limit - it configures CFS (Completely Fair Scheduler)
- Memory - ???
- Huge pages - ???

Q: What are the consequences of not specifying CPU and Memory limits at all?

# Links
- [Understanding resource limits in kubernetes: cpu time](https://medium.com/@betz.mark/understanding-resource-limits-in-kubernetes-cpu-time-9eff74d3161b)

---------------------------------
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>
