<div align="center"> WIKI </div>

**Paterns étudié :**

1. Objet composite
2. Injection de contrôle/dépendance

## Objet composite 

### Qu'est-ce qu'un objet composite ?

Un objet composite ou pattern composite (patron de conception en français) permet de gérer un ensemble d'objet.
En effet en java il est facile de gerer un objet a la fois mais quand il faut en gérer plusieurs en même temps ou même gerer un ensemble d'objet ca peut poser problème.

### Comment l'utiliser en JAVA ?

![exemple avec un diagramme](https://miro.medium.com/proxy/1*FpmtB3L4DTIoZUgLYqjz2g.webp)

Le composant déclare l'interface des objets qui rentre et implémente leur comportements. Il définit aussi une interface pour accéder aux composants enfants et les modifier.

Le composite définit le comportement des composant qui ont un composants enfants et vas les stockers puis implémenter leur opération.

Le client lui vas utiliser l'interface définit par le composant pour pouvoir manipuler les objets.

La feuille n'a pas d'enfants et elle définit le comportement des objets avec opération().

### Exemple concret :

```
public interface Department {
	void printDepartmentName();
}
```

On définit une interface Departement qui contient une fonction qui affiche le nom des départements.

Ensuite on vas définir 2 classes qui vont contenir toute les deux la méthode pour afficher le nom des départements mais elles ne contiennent pas d'autre objet de la classe département.


```
public class FinancialDepartment implements Department {
	private Integer id;
	private String name;
	public void printDepartmentName() {
		System.out.println(getClass().getSimpleName());
	}
	// standard constructor, getters, setters
}
```

```
public class SalesDepartment implements Department {
	private Integer id;
	private String name;
	public void printDepartmentName() {
		System.out.println(getClass().getSimpleName());
	}
	// standard constructor, getters, setters
}
```

Puis enfin une classe composite qui vas contenir plusieur élément de la Class Departement et en plus en rajouter ou supprimer avec (addDepartment, removeDepartment) en plus de la méthode pour afficher les noms de département 

```
public class HeadDepartment implements Department {
	private Integer id;
	private String name;
	private List<department> childDepartments;</department>
	public HeadDepartment(Integer id, String name) {
		this.id = id;
		this.name = name;
		this.childDepartments = new ArrayList<>();
	}
	public void printDepartmentName() {
		childDepartments.forEach(Department::printDepartmentName);
	}
	public void addDepartment(Department department) {
		childDepartments.add(department);
	}
	public void removeDepartment(Department department) {
		childDepartments.remove(department);
	}
}
```


## Injection de contrôle/dépendance 

C'est un patron de conception consistant à construire les dépendances d’un module hors de celui-ci, afin d’obtenir un maximum de contrôle. 
L'injection de dépendance est une forme de ce que l'on appelle inversion des contrôles. 
