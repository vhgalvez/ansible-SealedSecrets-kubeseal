# 🔐 ansible-SealedSecrets-kubeseal

Este repositorio contiene un rol de **Ansible** para instalar el binario [`kubeseal`](https://github.com/bitnami-labs/sealed-secrets) de **Bitnami Sealed Secrets** en sistemas Linux.  
`kubeseal` es una herramienta esencial para cifrar secretos antes de subirlos a un repositorio GitOps como **ArgoCD**.

---

## 📦 Características

- Instala la versión **v0.29.0** de `kubeseal`.
- Compatible con sistemas **RedHat, Debian, Alpine y Arch Linux**.
- Descarga, extrae y copia el binario a `/usr/local/bin/`.
- Verifica la instalación automáticamente.
- No requiere `Helm`, solo instala el binario en local o remoto.

---

## 📁 Estructura del repositorio

```bash
ansible-SealedSecrets-kubeseal/
├── inventory/
│   └── hosts.ini              # Inventario local o remoto
├── playbook.yml              # Playbook principal
├── roles/
│   └── kubeseal_installer/
│       └── tasks/
│           └── main.yml      # Tareas de instalación
├── LICENSE
└── README.md
```

---

## 🚀 Uso

### 1. Clonar el repositorio

```bash
# Clonar el repositorio
git clone https://github.com/vhgalvez/ansible-SealedSecrets-kubeseal.git
cd ansible-SealedSecrets-kubeseal
```

### 2. Configurar el inventario

#### Opción A: Instalar en localhost

```ini
# inventory/hosts.ini
[localhost]
127.0.0.1 ansible_connection=local
```

#### Opción B: Instalar en un nodo remoto

```ini
# inventory/hosts.ini
[masters]
10.17.4.21 ansible_host=10.17.4.21 ansible_user=core ansible_ssh_private_key_file=/root/.ssh/id_rsa
```

### 3. Ejecutar el playbook

```bash
# Ejecutar el playbook
sudo ansible-playbook -i inventory/hosts.ini playbook.yml
```

### ✅ Resultado esperado

Al finalizar, el binario `kubeseal` estará instalado en:

```bash
/usr/local/bin/kubeseal
```

Con verificación automática:

```bash
kubeseal --version
# kubeseal version: v0.29.0
```

---

## 🛠 Requisitos

- Python 3.x
- Ansible ≥ 2.10
- Acceso sudo si se instala en máquina local

---

## 📄 Licencia

Este proyecto está licenciado bajo la [MIT License](LICENSE).

---

## 🧠 Autor

Víctor Hugo Gálvez – [GitHub](https://github.com/vhgalvez)

---

## ⭐️ ¿Te fue útil?

¡Dale una ⭐ al repositorio para apoyar el proyecto!

---

### ✅ Commit sugerido

```bash
# Preparar el commit
git add README.md
git commit -m "📝 Mejora de documentación: guía completa de instalación para kubeseal v0.29.0"
git push origin main
```

¿Quieres que prepare también un `CHANGELOG.md` o lo dejamos así por ahora?