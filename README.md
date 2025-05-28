# 🔐 ansible-SealedSecrets-kubeseal

Este repositorio contiene un rol de Ansible para instalar el binario [`kubeseal`](https://github.com/bitnami-labs/sealed-secrets) de Bitnami Sealed Secrets en sistemas Linux. `kubeseal` es una herramienta esencial para cifrar secretos antes de subirlos a un repositorio GitOps, como ArgoCD.

---

## 📦 Características

- Instala la versión **v0.29.0** de `kubeseal`.
- Compatible con sistemas **RedHat, Debian, Alpine, Arch**.
- Descarga, extrae y coloca el binario en `/usr/local/bin/`.
- Verifica la instalación mostrando la versión.
- No requiere `Helm`, solo instala el binario localmente.

---

## 📁 Estructura del repositorio

```bash
ansible-SealedSecrets-kubeseal/
├── inventory/
│   └── hosts.ini            # Inventario local o remoto
├── playbook.yml            # Playbook principal
├── roles/
│   └── kubeseal_installer/
│       └── tasks/
│           └── main.yml    # Tareas de instalación
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

#### Opción B: Instalar en nodo remoto

```ini
# inventory/hosts.ini
[masters]
10.17.4.21 ansible_host=10.17.4.21 ansible_user=core ansible_ssh_private_key_file=/root/.ssh/id_rsa
```

### 3. Ejecutar el playbook

```bash
# Ejecutar el playbook
ansible-playbook -i inventory/hosts.ini playbook.yml
```

### ✅ Resultado esperado

Al finalizar, el binario `kubeseal` estará disponible en:

```bash
/usr/local/bin/kubeseal
```

Verificación automática incluida:

```bash
kubeseal --version
```

---

## 🛠 Requisitos

- Python 3.x
- Ansible ≥ 2.10
- Acceso sudo si se instala en máquina local

---

## 📄 Licencia

Este proyecto está bajo la licencia [MIT](LICENSE).

---

## 🧠 Autor

Víctor Hugo Gálvez – [GitHub](https://github.com/vhgalvez)

---

## ⭐️ ¿Te fue útil?

¡Dale una estrella al repositorio para apoyar el proyecto!