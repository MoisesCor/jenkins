FFROM php:7.1.17-apache
LABEL maintainer="Jaivic"

RUN a2enmod.bat rewrite

RUN powershell.exe -Command \
    Invoke-WebRequest -Uri "https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions.ps1" -OutFile "C:\\install-php-extensions.ps1"; \
    C:\\install-php-extensions.ps1 pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache pgsql; \
    Remove-Item C:\\install-php-extensions.ps1; \
    apt-get clean; \
    del -rf /var/lib/apt/lists/*

RUN powershell.exe -Command \
    Invoke-WebRequest -Uri "https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb" -OutFile "C:\\packages-microsoft-prod.deb"; \
    dpkg -i C:\\packages-microsoft-prod.deb; \
    apt-get update; \
    apt-get install -y powershell vim; \
    del -rf C:\\packages-microsoft-prod.deb

COPY . /var/www/html/
