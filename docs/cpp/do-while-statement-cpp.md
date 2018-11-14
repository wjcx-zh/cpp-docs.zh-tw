---
title: do-while 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: d930c1884975288ff11f4d4e5cf2728e717e17d5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326663"
---
# <a name="do-while-statement-c"></a>do-while 陳述式 (C++)

執行*陳述式*重複直到指定的終止條件 (*運算式*) 評估為零。

## <a name="syntax"></a>語法

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>備註

終止條件的測試會在迴圈中; 每次執行之後因此，**請勿-雖然**迴圈會執行一次以上，取決於終止運算式的值。 在陳述式主體中執行 [break](../cpp/break-statement-cpp.md)、[goto](../cpp/goto-statement-cpp.md) 或 [return](../cpp/return-statement-cpp.md) 陳述式時，**do-while** 陳述式也可能會終止。

*expression* 必須有算術或指標類型。 執行程序如下所示：

1. 會執行陳述式主體。

1. 接下來會評估 *expression*。 如果 *expression* 為 false，**do-while** 陳述式會終止，而並將控制權傳遞至程式中的下一個陳述式。 如果 *expression* 為 true (非零)，則會從步驟 1 開始重複處理序。

## <a name="example"></a>範例

下列範例會示範**請勿-雖然**陳述式：

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>另請參閱

[反覆運算陳述式](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[while 陳述式 (C++)](../cpp/while-statement-cpp.md)<br/>
[for 陳述式 (C++)](../cpp/for-statement-cpp.md)<br/>
[以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)