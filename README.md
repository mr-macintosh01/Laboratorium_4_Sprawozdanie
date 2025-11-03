# Laboratorium_4_Sprawozdanie

## Zadanie 1 — Utworzenie manifestu YAML dla Poda

Utworzono manifest YAML definiujący Poda loop, który wykonuje pętlę for i wypisuje pięć komunikatów.

### loop.yaml:

apiVersion: v1
kind: Pod
metadata:
  name: loop
spec:
  containers:
    - name: loop
      image: busybox:1.36.1
      command: ["sh", "-c", "for i in $(seq 1 5); do echo \"$i - A piece of cake !\"; done"]
  restartPolicy: Never
