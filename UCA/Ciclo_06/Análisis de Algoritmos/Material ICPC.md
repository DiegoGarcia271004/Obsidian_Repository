
> [!failure] Important
> Nunca olvidar el `endl`

**Mejorar entrada y salida**

```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

**Fenwick struct (XOR y SUM)**

```cpp
//XOR
struct Fenwick {
    vector<int> bit;
    int n;
    
    Fenwick(int n) : n(n) {
        bit.assign(n + 1, 0);
    }
    
    // Actualiza posición idx (1-indexado) con XOR del valor val
    void update(int idx, int val) {
        for (; idx <= n; idx += idx & -idx)
            bit[idx] ^= val;
    }
    
    // Devuelve XOR desde 1 hasta idx
    int query(int idx) {
        int res = 0;
        for (; idx > 0; idx -= idx & -idx)
            res ^= bit[idx];
        return res;
    }
    
    // Devuelve XOR en [l, r]
    int rangeXor(int l, int r) {
        return query(r) ^ query(l - 1);
    }
};

//SUM
struct Fenwick {
    int n;
    vector<long long> bit;
    Fenwick(int n) : n(n), bit(n + 1, 0) {}
    void update(int i, long long delta) {
        for (; i <= n; i += i & -i)
            bit[i] += delta;
    }

    long long query(int i) {
        long long res = 0;
        for (; i > 0; i -= i & -i)
            res += bit[i];
        return res;
    }

    long long rangeQuery(int l, int r) {
        return query(r) - query(l - 1);
    }
};

```

**Incluir todas las librerías en c++**

```c#
#include<bits/stdc++.h>
```


| Tipo                | Tamaño  | Comentario                                                                                                                                                                                                                               |
| ------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **int**           | 4 bytes | Opción predeterminada para los valores enteros.                                                                                                                                                                                          |
| **double**        | 8 bytes | Opción predeterminada para los valores de punto flotante.                                                                                                                                                                                |
| **bool**          | 1 byte  | Representa valores que pueden ser true o false.                                                                                                                                                                                          |
| **char**          | 1 byte  | Se utiliza en los caracteres ASCII de cadenas de estilo C antiguas u objetos std::string que nunca tendrán que convertirse a UNICODE.                                                                                                    |
| **wchar_t**       | 2 bytes | Representa valores de caracteres “anchos” que se pueden codificar en formato UNICODE (UTF-16 en Windows; puede diferir en otros sistemas operativos). **wchar_t** es el tipo de carácter que se usa en cadenas de tipo std::wstring. |
| **unsigned char** | 1 byte  | C++ no tiene un tipo byte integrado. Use **unsigned char** para representar un valor de byte.                                                                                                                                          |
| **unsigned int**  | 4 bytes | Opción predeterminada para los marcadores de bits.                                                                                                                                                                                       |
| **long long**     | 8 bytes | Representa un intervalo mucho mayor de valores enteros.                                                                                                                                                                                  |

| Tipo                   | Tamaño  | Rango de valores                   |
| ---------------------- | ------- | ---------------------------------- |
| **int**                | 4 bytes | -2,147,483,648 a 2,147,483,647     |
| **unsigned int**       | 4 bytes | 0 a 4,294,967,295                  |
| **double**             | 8 bytes | -9x10¹⁸ a 9x10¹⁸                   |
| **bool**               | 1 byte  | 0 a 1.8x10¹⁹                       |
| **char**               | 1 byte  | -128 a 127                         |
| **unsigned char**      | 1 byte  | 0 a 255                            |
| **long long**          | 8 bytes | los mismos que el long???          |
| **unsigned long long** | 8 bytes | los mismos que el unsigned long??? |

