# 🚀 Innovatech Chile - Arquitectura Cloud y DevOps

[![AWS EKS](https://img.shields.io/badge/AWS-EKS-orange?logo=amazon-aws)]()
[![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-blue?logo=github)]()
[![Spring Boot](https://img.shields.io/badge/Backend-Spring_Boot-green?logo=springboot)]()

---

## 📖 Descripción del Proyecto
Este repositorio centraliza la solución de orquestación para **Innovatech Chile**, una plataforma diseñada para la gestión de despachos y ventas. El proyecto se basa en una arquitectura de microservicios desplegada sobre **Amazon Elastic Kubernetes Service (EKS)**, automatizada mediante flujos de **CI/CD** que garantizan despliegues continuos, seguros y escalables.

---

## 🏗️ Arquitectura de la Solución
El sistema sigue un modelo de microservicios desacoplados:
* **Frontend:** Aplicación web que interactúa con el usuario final.
* **Backend (Ventas & Despachos):** APIs REST desarrolladas en Spring Boot que gestionan la lógica de negocio.
* **Infraestructura:** Todos los componentes se comunican dentro del clúster de Kubernetes, utilizando `ConfigMaps` y `Secrets` para la gestión de entornos.



---

## ⚙️ Flujo de Automatización (CI/CD)
Hemos implementado un pipeline de integración y despliegue continuo que elimina la intervención manual en el clúster.

1. **Continuous Integration (CI):** Se ejecutan pruebas automatizadas y la construcción de imágenes Docker al realizar `push` a la rama `main`.
2. **Container Registry:** Las imágenes se versionan y almacenan en **Amazon ECR**.
3. **Continuous Deployment (CD):** GitHub Actions interactúa con el clúster a través de `kubectl` para actualizar los deployments (`rollout restart`).

---

## 📂 Estructura del Repositorio
```text
.
├── .github/workflows/    # Pipelines de CI/CD (GitHub Actions)
├── front_despacho/       # Código fuente del Frontend
├── back-Ventas_SpringBoot/# Código fuente del Backend Ventas
├── back-Despachos_SpringBoot/# Código fuente del Backend Despacho
├── k8s/                  # Manifiestos de Kubernetes (YAMLs)
│   ├── deployment.yaml
│   ├── service.yaml
│   └── hpa.yaml          # Configuración de escalado automático
└── README.md
