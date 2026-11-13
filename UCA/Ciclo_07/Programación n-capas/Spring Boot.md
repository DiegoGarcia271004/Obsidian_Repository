Se realizará una aplicación backend con Spring con una base de datos en postgres

## Dependencias

[COMPLETAR]

## Aplicación

### Modelos

Para poder crear un modelo, se genera una clase, a la cuál se le aplicarán ciertas anotaciones que 
permitirá a spring a reconocer los datos

```Java
@Entity
@Table(name = "video_game")
public class Game (
	
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	public int Id;
	
	@Column
	public String Name;
	
	@Column
	public String Genre;
	
	@Column
	public String 
)
```
