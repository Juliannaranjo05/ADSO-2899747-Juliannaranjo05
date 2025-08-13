Práctica: Paso de Merge Request (MR) entre ambientes
Objetivo

Simular el flujo de cambios a través de los diferentes ambientes de trabajo (project → dev → qa → main), documentando cada paso.

Creación de ramas
# Desde main, crear las ramas qa, project y dev
git checkout main
git checkout -b qa
git checkout main
git checkout -b project
git checkout -b dev

Subida de ramas al repositorio remoto
git push -u origin dev
git checkout qa
git push -u origin qa
git checkout project
git push -u origin project

Cambios y commits por ambiente
1️⃣ Rama project
git checkout project
echo "Primer cambio desde rama project" > cambios.md
git add cambios.md
git commit -m "feat/docs: add initial change from project branch"
git push origin project

2️⃣ Rama dev
git checkout dev
echo "Validación en ambiente DEV" >> cambios.md
git add cambios.md
git commit -m "chore/docs: add DEV environment validation notes"
git push origin dev

3️⃣ Rama qa
git checkout qa
echo "Validación en ambiente QA" >> cambios.md
git add cambios.md
git commit -m "chore/docs: add QA environment validation notes"
git push origin qa

4️⃣ Rama main (Producción)
git checkout main
echo "Listo para producción" >> cambios.md
git add cambios.md
git commit -m "docs: mark changes ready for production"
git push origin main

Flujo de MR

MR: project → dev

MR: dev → qa

MR: qa → main

Deploy simulado a producción.

Archivo final cambios.md
Primer cambio desde rama project
Validación en ambiente DEV
Validación en ambiente QA
Listo para producción