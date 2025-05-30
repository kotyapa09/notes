# установка

```bash
sudo pacman -S docker
sudo systemctl start docker
sudo systemctl enable docker

# проверка версии
docker --version
# без необходимости вводить sudo перед каждой командой

sudo usermod -aG docker $USER
```

