I have made a directory in my Home folder. This directory is named "Notes" (with a capital N).
The files are .md files. This is required for me to open them in Obsidian.

I have opened the "Notes" directory as a Vault in Obsidian. So if I edit the files here, they will be edited in the Notes folder as well.

Now I initialized git with $\text{git init}$, and renamed the main branch with $\text{git branch -m main}$ .
$\text{vim README.md}$

$\text{git add README.md}$

$\text{git commit -m "Initial commit: added README.md"}$

$\text{git remote add origin git@github.com:NAME/REPO.git}$

$\text{git push -u origin main}$

Checking if the changes have been pushed: $\text{git status}$.

$\text{git add <filename.file>}$

