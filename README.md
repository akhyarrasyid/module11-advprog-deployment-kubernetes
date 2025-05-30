Advance Programming
# Module 11 - Deployment on Kubernetes 📘

- Nama    : Akhyar Rasyid Asy syifa
- Kelas   : Advance Programming - A
- NPM     : 2306241682

## Reflection 1: Hello Minikube
### 1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?

![img](images/logs-before-exposed.png)
![img](images/logs-after-exposed.png)
![img](images/logs-after-exposed(2).png)

Dapat dilihat bahwa terdapat perbedaan pada ketiga gambar tersebut. Gambar pertama menunjukkan keadaan log ketika belum meng-exposed sebagai service. Bisa dilihat bahwa sebelum aplikasi diekspos tsb, hanya terlihat adanya HTTP dan UDP yang dijalankan pada port 8080 (HTTP) dan port 8081 (UDP) saja. Sedangkan gambar kedua menunjukkan keadaan log ketika sudah meng-exposed sebagai service, lalu gambar ketiga juga sama menunjukkan keadaan log ketika sudah meng-exposed sebagai service tapi itu log ketika berkunjung untuk ke-2 kalinya. Log tersebut berisi aktivitas yang terjadi dari aplikasi yang berjalan di container, yaitu adanya server HTTP yang telah dimulai pada port tertentu dan diterimanya permintaan GET pada endpoint "/" beberapa kali. Jumlah log juga akan terus bertambah seiring banyaknya kita mencoba mengakses aplikasi tersebut. Hal tersebut dapat dilihat dari log permintaan GET yang terus bertambah.

### 2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`.What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?


Berdasarkan referensi dari [Namespace in Kubernetes
documentation](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/), penggunaan `-n` berfungsi untuk menspesifikasikan namespace yang akan dijadikan target. 

![img](images/tanpa-n.png)

Pada versi yang pertama (tanpa `-n`), perintah tersebut akan mengembalikan pods dan services dari namespace default yang ada di kluster Kubernetes,

![img](images/pakai-n.png)
sedangkan versi yang kedua ini dia (dengan `-n`) akan mengembalikan pods dan services dari namespace yang telah dispesifikasikan (dalam kasus ini "kube-system") saja. Misalnya,`kubectl get pods -n kube-system` akan mengembalikan pods yang ada di namespace kube-system.

