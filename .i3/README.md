- In `$HOME/.Xdefaults` `URxvt.geometry: 400x400` to fix terminal prompt spawning in the middle of the screen.
- For [zapret](https://github.com/bol-van/zapret), [source](https://btt.community/t/zapret-kullanarak-linux-icerisinde-erisim-engelli-siteleri-kullanmak/807):
  ```bash
  # change dns to 1.1.1.1 using nmtui
  sudo ./install_bin.sh
  sudo ./blockcheck.sh
  sudo ./install_easy.sh # <- replace necessary arguments here, e.g. change mode to nfqws and update with blockcheck's args.
  ```
- Setting up Python virtual environment:
  ```
  python -m venv envname
  source envname/bin/activate
  deactivate
  ```
