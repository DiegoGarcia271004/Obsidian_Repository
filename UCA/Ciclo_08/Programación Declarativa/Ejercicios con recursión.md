1. Realizar un contador de 1 a 10.
```prolog
contarA10(N) :-
	=:=(N, 10),
	writeln(N),
	!.

contarA10(N) :-
	=<(N, 10),
	witeln(N),
	is(N2, +(N,1)),
	contar1a10(N2).
```

2. Obtener factorial de N.
```prolog
factorial(0, 1) :- !.

factorial(N, F) :-
	>(N, 0),
	is(N1, -(N, 1)),
	factorial(N1, F1),
	is(F *(N, F1)).
```





