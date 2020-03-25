---
title: C++ 陳述式概觀
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: 9aba5deddca6fbf480cd9d573606b16b7ab047db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188424"
---
# <a name="overview-of-c-statements"></a>C++ 陳述式概觀

C++ 陳述式會依序執行，但運算式陳述式、選取陳述式、反覆項目陳述式或跳躍陳述式明確修改該序列時除外。

陳述式可以是下列任何一種類型：

```
labeled-statement
expression-statement
compound-statement
selection-statement
iteration-statement
jump-statement
declaration-statement
try-throw-catch
```

在大部分的情況下C++ ，語句語法與 ANSI C 相同。兩者的主要差異在於，在 C 中，只有在區塊開頭才允許宣告;C++加入宣告*語句*，這可有效地移除此限制。 這可讓您在程式中可以計算預先計算過的初始化數值時引入變數。

在區塊內部宣告變數也可讓您精確地控制這些變數的範圍和存留期。

陳述式的相關主題描述下列 C++ 關鍵字：

|||||
|-|-|-|-|
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|
|[case](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists](../cpp/if-not-exists-statement.md)|[try](../cpp/try-throw-and-catch-statements-cpp.md)|
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||
|[預設值](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||

## <a name="see-also"></a>另請參閱

[陳述式](../cpp/statements-cpp.md)
