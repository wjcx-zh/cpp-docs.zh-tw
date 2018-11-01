---
title: 程式終止中的 return 陳述式 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
ms.openlocfilehash: 9c7b6130ee1a0b49ab75a70d84764d3a1f8c5ef0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613040"
---
# <a name="return-statement-in-program-termination-c"></a>程式終止中的 return 陳述式 (C++)

發出**會傳回**陳述式，從`main`功能上相當於呼叫`exit`函式。 參考下列範例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit`並**傳回**在上述範例中的陳述式會在功能上完全相同。 不過，c + + 需要具有函式傳回型別以外**void**傳回值。 **會傳回**陳述式可讓您傳回值，以從`main`。

## <a name="see-also"></a>另請參閱

[程式終止](../cpp/program-termination.md)