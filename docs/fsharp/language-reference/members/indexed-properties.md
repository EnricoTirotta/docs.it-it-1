---
title: "Proprietà indicizzate (F#)"
description: "Informazioni sulle proprietà indicizzate F # che sono proprietà che forniscono l'accesso di tipo matrice ai dati ordinati."
keywords: visual f#, f#, programmazione funzionale
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f1266b8b-e2e3-4f49-9332-65c6d34dc0f3
ms.openlocfilehash: 78a09a70621e82f073346471e68ec826359641d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="indexed-properties"></a>Proprietà indicizzate

*Proprietà indicizzate* vengono ordinate in proprietà che forniscono l'accesso di tipo matrice ai dati.


## <a name="syntax"></a>Sintassi

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>Note
Le tre forme di sintassi precedente viene illustrato come definire proprietà indicizzate che hanno entrambi un `get` e un `set` (metodo), hanno un `get` solo, metodo o un `set` solo metodo. È possibile combinare la sintassi illustrata solo per get e la sintassi illustrata solo per set e produrre una proprietà che contiene sia get che set. Questo modulo di quest'ultimo consente di inserire gli attributi e modificatori di accessibilità diversi su get e set di metodi.

Quando il *PropertyName* è `Item`, il compilatore considera la proprietà come una proprietà indicizzata predefinita. Oggetto *proprietà indicizzata predefinita* è una proprietà che è possibile accedere tramite la sintassi di tipo matrice sull'istanza dell'oggetto. Ad esempio, se `obj` è un oggetto del tipo che definisce questa proprietà, la sintassi `obj.[index]` viene utilizzato per accedere alla proprietà.

La sintassi per l'accesso a una proprietà indicizzata è fornire il nome della proprietà e l'indice racchiuso tra parentesi. Ad esempio, se la proprietà è `Ordinal`, si scrive `obj.Ordinal(index)` per accedervi.

Indipendentemente dal modulo utilizzato, è necessario utilizzare sempre il form sottoposte a currying per il `set` metodo su una proprietà indicizzata. Per informazioni sulle funzioni sottoposte a currying, vedere [funzioni](../functions/index.md).

## <a name="example"></a>Esempio

Esempio di codice seguente viene illustrata la definizione e utilizzo di predefinite e proprietà indicizzate non predefinite con get e set di metodi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>Output

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>Proprietà indicizzate con più variabili di indice
Proprietà indicizzate possono avere più di una variabile di indice. In tal caso, le variabili sono separate da virgole quando la proprietà viene utilizzata. Il metodo set in tale proprietà deve avere due argomenti sottoposti a currying, il primo dei quali è una tupla contenente le chiavi e il secondo dei quali è il valore da impostare.

Il codice seguente viene illustrato l'utilizzo di una proprietà indicizzata con più variabili di indice.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a>Vedere anche
[Membri](index.md)
