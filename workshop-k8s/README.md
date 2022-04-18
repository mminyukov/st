# Установить до начала workshop

## kubectl

Официальная документация по установке kubectl [тут](https://kubernetes.io/ru/docs/tasks/tools/install-kubectl/).

### Для пользователей linux или WSL
```bash
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

kubectl version --client
```

Перейдите в домашнюю директорию и создайте директорию `.kube`:
```bash
cd $HOME
mkdir .kube
```
После необходимо добавить в `.kube` файл `config`


### Для пользователей windows
__Установка двоичного файла kubectl__
```powershell
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.23.0/bin/windows/amd64/kubectl.exe
```
Переместите двоичный файл в директорию из переменной окружения PATH

__Установка kubectl с помощью Chocolatey__
Устанока Chocolatey
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
Установка kubectl
```powershell
choco install kubernetes-cli
```

Перейдите в домашнюю директорию и создайте директорию `.kube`:
```powershell
cd %USERPROFILE%
mkdir .kube
```

После необходимо добавить в `.kube` файл `config`

## helm
### Для пользователей linux или WSL
```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

### Для пользователей windows
__Установка helm с помощью Chocolatey__
```powershell
choco install kubernetes-helm
```

# Основные команды kubectl
Шпаргалка по [kubectl](https://kubernetes.io/ru/docs/reference/kubectl/cheatsheet/)

Изменить путь до config файла через переменную окружения
```
export KUBECONFIG=<PATH TO FILE CONFIG>
```

Посмотреть текущие настройки подключения
```
kubectl config view
```

Сменить контекст
```
kubectl config set-context --current --namespace=<NAMESPACE>
```

Получить список нод
```
kubectl get nodes
```

Получить список ресурсов kubernetes
```
kubectl api-resources
```

Посмотреть список запущенных ресурсов
```
kubectl get <API-RESOURCE>
```

Посмотреть список запущенных ресурсов в конкретном namespace
```
kubectl -n <NAMESPACE> get <API_RESOURCE>
```

Применить манифест
```
kubectl apply -f <FILE NAME>
```

Удалить все ресурсы описанные в манифесте
```
kubectl delete -f <FILE NAME>
```

Посмотреть подробное описание ресурса
```
kubectl describe <API-RESOURCE> <RESOURCE NAME>
```

Посмотреть логи pod
```
kubectl logs <POD NAME>
```

Выполнить команду внутри контейнера запущенного в pod
```
kubectl exec -ti <POD NAME> -- <COMMAND>
```

# Основные команды helm
Посмотреть список release
```
helm list
```

Отрендерить шаблон для просмотра итогового yaml
```
helm template <CHART PATH>
```

Установить release
```
helm install <CHART PATH>
```

Удалить release
```
helm uninstall <CHART PATH>
```
