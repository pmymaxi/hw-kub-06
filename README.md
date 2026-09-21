# Настройка приложений и управление доступом в Kubernetes

## Задание 1: Работа с ConfigMaps
Манифесты: 
- deployment.yaml
- configmap-web.yaml
- service.yaml

<img width="574" height="346" alt="hw-kub-06-01" src="https://github.com/user-attachments/assets/b180c38e-6e22-41b4-a96b-0560b549619a" />

## Задание 2: Настройка HTTPS с Secrets
Манифесты: 
- secret-tls.yaml
- ingress-tls.yaml
  
### Генерация сертификата
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=myapp.example.com"
```
<img width="735" height="217" alt="hw-kub-06-02" src="https://github.com/user-attachments/assets/9b719148-abfd-4455-9b92-46116026ceba" />

## Задание 3: Настройка RBAC
Манифесты: 
- role-pod-reader.yaml
- rolebinding-developer.yaml

### Команды генерации сертификатов
- Генерируем приватный ключ пользователя pmymaxi:
```bash
openssl genrsa -out developer.key 2048
```
- Создаём CSR запрос на выпуск сертификата:
```bash
openssl req -new key developer.key -out developer.csr -subj "/CN=pmymaxi"
```
- Подписываем запрос на выпуск сертификата пользователя pmymaxi:
```bash
openssl x509 -req -in developer.csr -CA /var/snap/microk8s/current/certs/ca.crt -CAkey /var/snap/microk8s/current/certs/ca.key -CAcreateserial -out developer.crt -days 365
```
<img width="540" height="349" alt="hw-kub-06-03" src="https://github.com/user-attachments/assets/0c07a09c-bf9c-452f-b623-1fc6f433e431" />



