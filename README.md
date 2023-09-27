
# MongoDB ve Express Projesi README

Bu README dosyası, MongoDB ve Express kullanarak oluşturulan bir projenin temel yapılandırması ve nasıl başlatılacağı hakkında bilgi içerir. Projenin başarılı bir şekilde çalıştırılması için aşağıdaki adımları izleyebilirsiniz.

## Gereksinimler

Projenin başlatılması için aşağıdaki gereksinimlere ihtiyacınız vardır:

- Kubernetes Kubernetes Cluster'a erişim.
- `kubectl` komut satırı aracının yüklü olması.
- MongoDB ve Express ile ilgili YAML dosyalarınızın hazır olması.

## Kurulum Adımları

1. Kubernetes Cluster'a Bağlanma

   Kubernetes Cluster'a bağlanmak için terminalde aşağıdaki komutu kullanın:

   ```bash
   kubectl config use-context [cluster_adı]
   ```

2. MongoDB ve Express Deployment'ları Oluşturma

   Öncelikle MongoDB ve Express Deployment'larını oluşturun:

   ```bash
   kubectl apply -f [mongodb-ve-express-deployment-yaml-dosyası]
   ```

3. MongoDB ve Express Servislerini Oluşturma

   Servislerinizi oluşturmak için aşağıdaki komutu kullanın:

   ```bash
   kubectl apply -f [mongodb-ve-express-servis-yaml-dosyası]
   ```

4. Secret ve ConfigMap Oluşturma

   Projenizin çalışması için gizli bilgileri ve yapılandırmaları içeren Secret ve ConfigMap'leri oluşturun:

   ```bash
   kubectl apply -f [secret-yaml-dosyası]
   kubectl apply -f [configmap-yaml-dosyası]
   ```

5. MongoDB ve Express Uygulamalarını Başlatma

   MongoDB ve Express uygulamalarını başlatmak için aşağıdaki komutu kullanın:

   ```bash
   kubectl create deployment [mongodb-deployment-adı] --image=mongo
   kubectl create deployment [express-deployment-adı] --image=mongo-express
   ```

6. Hizmetleri Erişilebilir Kılma

   Express servisinin erişilebilir olması için bir LoadBalancer hizmeti oluşturun:

   ```bash
   kubectl expose deployment [express-deployment-adı] --type=LoadBalancer --port=8081
   ```

   Bu komut, Express uygulamanızın dış IP adresine ve belirtilen port numarasına bağlanmasını sağlar.

7. Uygulamaya Erişim

   Projenizin çalıştığını doğrulamak için aşağıdaki URL'yi kullanabilirsiniz:

   ```
   http://[external-ip]:8081
   ```

   `[external-ip]` kısmı, LoadBalancer hizmetinizin dış IP adresi olacaktır.

Bu adımları izlediğinizde MongoDB ve Express uygulamanız Kubernetes üzerinde başlamalıdır. Başka herhangi bir sorunuz veya ek talimatlarınız varsa, lütfen sorunuzu belirtin.
