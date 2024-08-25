Ingress Controller için helm dışında başka bir indirme yöntemi tercih ediyorsanız, buradan istediğiniz yöntemi [detaylı bulabilirsiniz](https://kubernetes.github.io/ingress-nginx/deploy/).

Helm ile Kubernetes üzerinde `ingress-nginx` adlı Ingress denetleyicisini kurmak için aşağıdaki komutu kullanın:

```bash
helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace
```

## Repositry'nin Clonelanması

## YAML Dosyalarının Uygulanması
Clone edilen repoya gidin ve Kubernetes YAML dosyalarınızı uygulayın:
```
cd k8s/
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
```

## Hosts Dosyasının Konfigürasyonu
Ingress kaynak tanımı, Kubernetes üzerinde bir uygulamayı yönlendirmek için kullanılır ve genellikle bir alan adı (host) ile eşleştirilir. Bu örnekte flaskapp.localhost adlı bir alan adı kullanılmıştır. Bilgisayarınızda bu alan adını doğru şekilde yönlendirmek için hosts dosyanıza bir ekleme yapmanız gerekmektedir.


Windows
```
C:\Windows\System32\drivers\etc\hosts dosyasını bir metin düzenleyici (örneğin Notepad veya Notepad++) ile açın.

Dosyanın en altına şu satırı ekleyin:

127.0.0.1   flaskapp.local
```

Mac veya Linux
Terminali açın.
```
sudo nano /etc/hosts komutunu kullanarak hosts dosyasını açın (veya sudo vim /etc/hosts gibi başka bir metin düzenleyici kullanabilirsiniz).

Dosyanın en altına şu satırı ekleyin:

127.0.0.1   flaskapp.local

```
Dosyayı kaydedin ve kapatın.

Browserınız'da flaskapp.local sayfasına giderek Hello World yazısı ile karşılacaksınız.


### Replica Setlerin Sayılarının Değiştirilmesi
Deploymentımınzda bulunan replica setlerin sayısını 2den 5e çıkarabiliriz
``` 
kubectl scale deployment flask-helloworld --replicas=5
```

