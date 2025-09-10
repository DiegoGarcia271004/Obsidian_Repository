1. Suponga que tiene una bolsa en la cuál se colocan las 15 bolas de billar, a continuación procede a sacar dos bolas consecutivamente. ¿De cuántas maneras puede sacar dos bolas si solamente se cuentan los intentos en los cuales la segunda es la menor?
2. En un torneo de ajedrez participan **30 jugadores**. Se sabe que:

	- **18 jugadores** saben programar en Python.
    
	- El resto no lo sabe.
	Si queremos elegir a un jugador **que no sepa programar en Python**, ¿de cuántas formas distintas se puede hacer la selección?

3. En una encuesta a **120 estudiantes**, se encontró lo siguiente:

- **60 estudian inglés.**
    
- **45 estudian francés.**
    
- **30 estudian alemán.**
    
- **20 estudian inglés y francés.**
    
- **15 estudian inglés y alemán.**
    
- **10 estudian francés y alemán.**
    
- **5 estudian los tres idiomas.**
    

Pregunta:  
a) ¿Cuántos estudiantes estudian **al menos un idioma**?  
b) ¿Cuántos estudian **exactamente un idioma**?  
c) ¿Cuántos no estudian ningún idioma?
d) ¿Cuántos estudiantes estudian exactamente dos idiomas?
e) ¿Cuántos estudiantes estudian exactamente 3 idiomas?

![[Ej3LitA1|center]]
a) 
Para encontrar la gente que estudia al menos un idioma, podemos sumar la cantidad total de personas que estudian cada idioma, y restarle las intersecciones para que no se sobrepongan

$$
|I \cup F\cup A|=(60+30+45)-(20+15+10)+5=95
$$

b)
Encontrando cuantos estudiantes hay en cada idioma:
- Solo Inglés: $|I|-|I\cap F|-|I\cap A|+|I\cap F\cap A|=60-20-15+5=30$
- Solo Francés: $|F|-|F\cap I|-|F\cap A|+|F\cap I\cap A|=45-20-10+5=20$
- Solo Alemán: $|A|-|A\cap I|-|A\cap F|+|A\cap F\cap I|=30-15-10+5=10$
Sumando todos los grupos:
$$
\boxed{60}
$$

