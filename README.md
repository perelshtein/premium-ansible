Подготовка VPS-сервера на Ubuntu 22.04-24.04 к установке PremiumExchanger.
Для криптовалютных обменников.
---
Выполняются задачи:
- настройка входа по ключу через SSH;
- настройка ufw и fail2ban;
- установка PHP и ioncube;
- установка MySQL, сохранение пароля на локальной машине;
- получение сертификата через certbot (DNS должен управляться через CloudFlare);
- установка nginx и создание виртуального хоста (сайта).

70% работы сделано!
Платная панель управления (как написано в руководстве) не нужна!

Дальше останется скачать установщик и лицензию PremiumExchanger, закинуть в /var/www/{domain}. Провести установку. Настроить cron для обновл курсов.


Первый запуск:
---
- редактируем inventory.yaml, надо задать переменные my_server и domain;
- ansible-playbook exchanger.yaml -i inventory.yaml --extra-vars "root_pass=my_server_pass" --extra-vars "cloudflare_token=my_cf_token"
- ansible-galaxy collection install -r requirements.yaml

Последующие запуски:
---
ansible-playbook exchanger.yaml -i inventory.yaml
