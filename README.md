# Laboratorium_4_Sprawozdanie

## Zadanie 1 — Utworzenie manifestu YAML dla Poda

Utworzono manifest YAML definiujący Poda loop, który wykonuje pętlę for i wypisuje pięć komunikatów.

### <code>loop.yaml</code>:


<code>apiVersion: v1
kind: Pod
metadata:
  name: loop
spec:
  containers:
    - name: loop
      image: busybox:1.36.1
      command: ["sh", "-c", "for i in $(seq 1 5); do echo \"$i - A piece of cake !\"; done"]
  restartPolicy: Never
</code>

## Zadanie 2 — Utworzenie Poda i sprawdzenie statusu

Pod loop wykonał polecenie i zakończył działanie ze statusem Completed, ponieważ proces w kontenerze zakończył się po wypisaniu pięciu linii.

### Uruchomienie Poda <code>kubectl apply -f loop.yaml</code>:

<img width="416" height="60" alt="image" src="https://github.com/user-attachments/assets/61a522f1-09dc-43e8-a2f1-d7ebd18bf992" />

### Sprawdzenie statusu <code>kubectl get pods</code>:

<img width="497" height="76" alt="image" src="https://github.com/user-attachments/assets/e660acec-bc43-4812-9704-c346658b3167" />

### Logi <code>kubectl logs loop</code>:

<img width="477" height="144" alt="image" src="https://github.com/user-attachments/assets/31950bd9-c0ed-4895-a8b1-675c04f6b75f" />

## Zadanie 3 — Modyfikacja manifestu, aby Pod był w stanie Running:

Po dodaniu <code>sleep infinity</code> proces w kontenerze nie kończy się, dzięki czemu Pod pozostaje w stanie Running.

### Zmieniony plik <code>loop.yaml</code>:

<code>apiVersion: v1
kind: Pod
metadata:
  name: loop
spec:
  containers:
    - name: loop
      image: busybox:1.36.1
      command: ["sh", "-c", "for i in $(seq 1 5); do echo \"$i - A piece of cake !\"; done; sleep infinity"]
  restartPolicy: Never
</code>

### Sprawdzenie statusu <code>kubectl get pods</code>:

<img width="411" height="86" alt="image" src="https://github.com/user-attachments/assets/95e4aed1-3815-49bd-9170-b0f7ce1d92ec" />

### <code>kubectl logs loop</code>:

<img width="369" height="69" alt="image" src="https://github.com/user-attachments/assets/b0efe6c9-0141-4b96-aab5-73a805c1ea62" />
