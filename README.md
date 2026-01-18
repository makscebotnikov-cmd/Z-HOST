# Домашнее задание к занятию  «Защита хоста» - `Чеботников М.Б.`

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

---

### Задание 1
1. Установите eCryptfs.
2. Добавьте пользователя cryptouser.
3. Зашифруйте домашний каталог пользователя с помощью eCryptfs.
В качестве ответа пришлите снимки экрана домашнего каталога пользователя с исходными и зашифрованными данными.

#### ОТВЕТ:
`Код:`
1.
```
sudo apt install ecryptfs-utils
```
2.
```
sudo adduser cryptouser
sudo ls -la /home/cryptouser/
```

<img width="452" height="94" alt="1" src="https://github.com/user-attachments/assets/552f854b-855a-4080-aa41-c89fbb62e6dd" />


3.
```
sudo ecryptfs-migrate-home -u cryptouser
sudo ls -la /home/cryptouser/
```
<img width="721" height="350" alt="2" src="https://github.com/user-attachments/assets/f6cb6a0a-b477-4462-8810-e6ebd70732cf" />


<img width="804" height="108" alt="3" src="https://github.com/user-attachments/assets/e5518575-3d4d-4f5c-ac2a-45fd5d0d196b" />



---

### Задание 2
1. Установите поддержку LUKS.
2. Создайте небольшой раздел, например, 100 Мб.
3. Зашифруйте созданный раздел с помощью LUKS.
В качестве ответа пришлите снимки экрана с поэтапным выполнением задания.

#### ОТВЕТ:
`Код:`
```
dd if=/dev/zero of=/home/user-test/home-13-2.img bs=1M count=100
ls -lh /home/user-test/home-13-2.img 

sudo cryptsetup luksFormat /home/user-test/home-13-2.img
sudo cryptsetup open /home/user-test/home-13-2.img my_iso_crypt
sudo mkfs.ext4 /dev/mapper/my_iso_crypt

sudo mkdir /mnt/iso-crypt
sudo mount /dev/mapper/my_iso_crypt /mnt/iso-crypt
echo "Makhovskiy VS" | sudo tee /mnt/iso-crypt/test-home-13-2.txt

sudo umount /mnt/iso-crypt
sudo cryptsetup luksDump /home/user-test/home-13-2.img
hexdump -C /home/user-test/home-13-2.img | head -n 20
```

<img width="526" height="313" alt="4" src="https://github.com/user-attachments/assets/ca5c4f3d-3552-4061-9880-fcda38b6541a" />


<img width="468" height="576" alt="5" src="https://github.com/user-attachments/assets/9c12ac20-e133-4cdc-9603-02fa47609747" />


<img width="452" height="273" alt="6" src="https://github.com/user-attachments/assets/d7eee52a-6cb0-4896-97a7-361a363a3324" />


---

Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале

### Задание 3 *
1. Установите apparmor.
2. Повторите эксперимент, указанный в лекции.
3. Отключите (удалите) apparmor.
В качестве ответа пришлите снимки экрана с поэтапным выполнением задания.

#### ОТВЕТ:


---
