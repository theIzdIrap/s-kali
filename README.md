# s-kali

V0.2.1

## [2025-07-20] Firewall Konfigürasyonu

- OUTPUT policy DROP olarak ayarlandı.
- Tor servisi (UID 126) için çıkış izni verildi.
- Kullanıcı `kali` (UID 1000) için çıkış izni verildi.
- root (UID 0) için çıkış izni verildi.
- Sistem servisleri için gerekli UID’ler whitelist’e eklendi (örn: 124, 123, 985, 991, 992).
- 127.0.0.1 hedefli trafik izinli bırakıldı.
- RELATED, ESTABLISHED bağlantılar kabul edildi.
- Kullanıcı oturumundaki GNOME servisleri engellenmedi.
- `iptables` kuralları kalıcı yapılmadı, geçici olarak uygulandı.

## [2025-07-20] MAC Adresi Rastgeleleştirme

- `macchanger.sh` servisi oluşturuldu.
- Her 3 saniyede bir rastgele MAC adresi üretimi eklendi.
- `systemd` servisi ile otomatik başlatma sağlandı.
- Reboot sonrası otomatik başlatma desteği eklendi.
- Ağ arayüzü her değişim sonrası otomatik yeniden başlatılıyor (`ifconfig down/up`).
- `journalctl` üzerinden log takibi yapılabilir.
- `Tor` yönlendirmesiyle birlikte entegre kullanım için optimize edildi.


## [2025-07-20] Tor IP Adresi Değiştirme Servisi

- `ipchanger.sh` adında bir script oluşturuldu.
- Her 3 saniyede IP adresi değiştiriyor.
- Her çalıştırıldığında yeni bir Tor devresi (circuit) oluşturularak dış IP değiştiriliyor.
- `controlport` üzerinden Tor ağına `NEWNYM` komutu gönderiliyor.
- `systemd` servisi tanımlandı: reboot sonrası otomatik başlıyor.
- Diğer trafikle karışmaması için yalnızca Tor ile yönlendirilen servisler bu scriptten etkileniyor.
- `nyx` ya da `curl ifconfig.me` ile IP değişimi doğrulanabilir.
- MAC değişim servisi (`macchanger.sh`) ve `iptables` ile birlikte entegre güvenlik sağlandı.
