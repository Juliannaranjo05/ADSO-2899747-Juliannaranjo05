# Concepto y Práctica de Merge Request (MR)

## 1. Concepto de Merge Request (MR)

Un **Merge Request (MR)** es una solicitud para integrar cambios realizados en una rama de desarrollo hacia otra rama objetivo dentro de un repositorio, generalmente después de haber completado una funcionalidad o corregido un error.  
Este proceso permite que otros miembros del equipo revisen el código antes de integrarlo, garantizando **calidad**, **consistencia** y **reducción de errores**.

---

## 2. Ambientes de trabajo en un flujo típico

Un flujo de desarrollo profesional suele dividirse en varios ambientes:

### Desarrollo (**DEV**)
- Donde los programadores crean y prueban nuevas funcionalidades.
- Código inestable y en constante cambio.

### Pruebas / **QA**
- Aquí se valida que las nuevas funcionalidades funcionen como se espera.
- Pruebas unitarias, integraciones y reportes de bugs.

### Preproducción (**STAGING**)
- Replica casi idéntica del ambiente de producción.
- Última validación antes de liberar a usuarios finales.

### Producción (**PROD**)
- Ambiente real donde los usuarios interactúan con el producto.
- Cambios deben llegar aquí solo después de pasar todas las validaciones.

---

## 3. Gráfico del proceso de MR entre ambientes

- [ Rama de Funcionalidad ]
- |
- (MR a DEV)
- ↓
- DEV ----> QA ----> STAGING ----> PROD
- | | | |
- Revisión Validación Última Usuarios
- inicial técnica revisión finales


**Explicación del flujo:**
1. El desarrollador crea un MR para pasar cambios desde la rama de funcionalidad hacia **DEV**.  
2. Una vez aprobados en **DEV**, se hace un nuevo MR hacia **QA** para validaciones.  
3. Si todo está correcto, se pasa mediante MR a **STAGING** para simulación real.  
4. Finalmente, se hace el MR a **PROD** para que los cambios lleguen al entorno en vivo.

---

## 4. Práctica: Paso de MR entre ambientes

**Ejemplo de flujo práctico:**

1. **Crear rama de funcionalidad:**
   ```bash
   git checkout -b feature/nueva-funcion