# bakup via tasker

- installation steps:
  - install tasker (android)
  - install tasker rsync: apk from https://github.com/ribbons/TaskerRsync/
  - give special permission full file controll to tasker
- setup tasker:
  - profiles (when to trigger someting)
    - profileA with wlan A AND time, trigger task sync
    - profileB with wlan B AND time, trigger task sync
  - tasks (what to do in which order)
    - keys (used once only)
      - step create priv key 
      - step get pub key 
      - step set var %pubkey to %PubKey2
    - sync
      - example how a step should look like:
        - "-e 'ssh -p %TargetPort' -rva /sdcard/Documents/ %User@%TargetHost:%TargetBasePath/Documents
        - note: trailing slash for source: all files under source
        - use KnownHosts var in tasker in known_hosts field for steps, 
    - step documents
    - step tasks.org
    - step whatsapp
    - step signal
    - step pictures
    - step dcim
  - vars
    - TargetHost
    - TargetPort
    - User eg rsync_backup
    - KnownHosts (see below with ssh-keyscan)
    - TargetBasePath (excluding trailing slash)
- one time setup steps:
  - read %Pubkey2 from vars (after keys task) and append to nas user on /var/services/homes/yourUser/.ssh/authorized_keys
  - get ssh public key of nas via ssh-keyscan -p yourPort yourHost, add as varibble BUT use the %TargetHost as prefix. Eg "192.168... ssh-ed25519 AAAAC..."

