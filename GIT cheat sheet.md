.
- Ver git-cheat-sheet-education.pdf

### Git Cheat Sheet

#### **Configuración Inicial**

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@example.com"
git config --list  # Ver configuración actual
```

#### **Crear un Repositorio**

```bash
git init  # Inicializar un repositorio
git clone <url>  # Clonar un repositorio existente
```

#### **Estado del Repositorio**

```bash
git status  # Ver cambios y estado del repositorio
git diff  # Mostrar diferencias entre archivos
git log  # Ver historial de commits
git log --stat  # Ver historial con detalles de cambios
```

#### **Añadir y Confirmar Cambios**

```bash
git add <archivo>  # Añadir archivos al área de preparación
git add .  # Añadir todos los archivos
git commit -m "Mensaje del commit"  # Realizar un commit
git commit --amend  # Editar el último commit
```

#### **Ver Cambios y Diferencias**

```bash
git diff  # Ver cambios no añadidos al área de preparación
git diff --staged  # Ver cambios ya añadidos al área de preparación
git show <commit>  # Ver detalles de un commit específico
```

#### **Ramas (Branches)**

```bash
git branch  # Listar ramas locales
git branch <nombre_rama>  # Crear una nueva rama
git checkout <nombre_rama>  # Cambiar de rama
git checkout -b <nombre_rama>  # Crear y cambiar a una nueva rama
git merge <nombre_rama>  # Fusionar una rama con la actual
git branch -d <nombre_rama>  # Eliminar una rama local
```

#### **Restaurar y Revertir Cambios**

```bash
git checkout -- <archivo>  # Restaurar archivo modificado
git reset --soft HEAD~1  # Deshacer el último commit, conservando cambios
git reset --hard HEAD~1  # Deshacer el último commit y cambios
git revert <commit>  # Revertir un commit
```

#### **Revisión de Cambios**

```bash
git log --oneline  # Ver historial simplificado
git reflog  # Ver todos los cambios de referencia
git show <commit>  # Mostrar detalles de un commit
```

#### **Trabajo con Repositorios Remotos**

```bash
git remote add origin <url>  # Añadir un repositorio remoto
git remote -v  # Ver repositorios remotos
git push origin <rama>  # Subir cambios al repositorio remoto
git pull origin <rama>  # Descargar cambios del repositorio remoto
git fetch origin  # Descargar sin fusionar
git push -u origin <rama>  # Subir y vincular una rama local al remoto
```

#### **Cherry-pick**

```bash
git cherry-pick <commit>  # Aplicar un commit específico de otra rama
```

#### **Reset**

```bash
git reset --soft <commit>  # Mover el HEAD al commit y conservar cambios en staging
git reset --mixed <commit>  # Mover el HEAD y quitar los cambios del área de preparación
git reset --hard <commit>  # Mover el HEAD y eliminar todos los cambios
```

#### **Stash (Guardar cambios temporalmente)**

```bash
git stash  # Guardar los cambios sin hacer commit
git stash pop  # Aplicar el último stash y eliminarlo
git stash apply  # Aplicar un stash sin eliminarlo
git stash list  # Listar stashes guardados
git stash drop  # Eliminar un stash específico
```

#### **Submódulos**

```bash
git submodule add <url>  # Añadir un submódulo
git submodule update --init  # Inicializar y actualizar submódulos
```

#### **Buenas Prácticas**

- Hacer commits pequeños y frecuentes.
- Usar ramas para nuevas funcionalidades.
- Escribir mensajes de commit descriptivos.
- Revisar código antes de hacer un merge.

