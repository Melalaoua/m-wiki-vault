tags:: #thelaboratory/howto 
source:: [1](https://cpu.land/how-to-run-a-program)
## How to run a Program.
Dans cette section, nous allons nous intéresser au kernel Linux afin de comprendre comment les programmes sont chargés et exécutés.

On se concentre spécifiquement sur Linux en x86-64, pourquoi ?
- Linux est un OS ordinateur, mobile, server avec beaucoup de features. Il est open source, c'est donc super facile de rechercher des choses, il faut juste lire le code.
- x86_64 est l'architecture la plus moderne sur ordinateurs, beaucoup de codes tournent dessus.

### Comportement basique d'un Exec Syscalls.

![[Pasted image 20230827094451.png]]

Commencons par le syscall le plus important : ``execve``. Il charge le programme et, si il est effectivement bien chargé, remplace le processus actuel avec le processus qu'il vient de charger. Autres syscalls (``execlp, excvpe, etc..``) existent, mais ils sont une couche mise par dessus execve.

> **Aside: `execveat`**

> `execve` is _actually_ built on top of `execveat`, a more general syscall that runs a program with some configuration options. For simplicity, we’ll mostly talk about `execve`; the only difference is that it provides some defaults to `execveat`.

> Curious what `ve` stands for? The `v` means one parameter is the vector (list) of arguments (`argv`), and the `e` means another parameter is the vector of environment variables (`envp`). Various other exec syscalls have different suffixes to designate different call signatures. The `at` in `execveat` is just “at”, because it specifies the location to run `execve` at.

La signature de execve est 
```
int execve(const char *filename, char *const argv[], char *const envp[]);
```

- The `filename` argument specifies a path to the program to run.
- `argv` is a null-terminated (meaning the last item is a null pointer) list of arguments to the program. The `argc` argument you’ll commonly see passed to C main functions is actually calculated later by the syscall, thus the null-termination.
- The `envp` argument contains another null-terminated list of environment variables used as context for the application. They’re… conventionally `KEY=VALUE` pairs. _Conventionally._ I love computers.

