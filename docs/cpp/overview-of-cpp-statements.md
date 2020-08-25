---
title: C++ 陳述式概觀
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
ms.openlocfilehash: d6bd6b5bb7ba4b83fbed63a40fecc8194cb3707a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832421"
---
# <a name="overview-of-c-statements"></a>C++ 陳述式概觀

C++ 陳述式會依序執行，但運算式陳述式、選取陳述式、反覆項目陳述式或跳躍陳述式明確修改該序列時除外。

陳述式可以是下列任何一種類型：

> *`labeled-statement`*\
> *`expression-statement`*\
> *`compound-statement`*\
> *`selection-statement`*\
> *`iteration-statement`*\
> *`jump-statement`*\
> *`declaration-statement`*\
> *`try-throw-catch`*

在大部分的情況下，c + + 語句語法與 ANSI C89 的語法相同。 兩者之間的主要差異在於，在 C89 中，只允許在區塊開頭使用宣告;C + + 加入 *`declaration-statement`* ，可有效地移除此限制。 這可讓您在程式中可以計算預先計算過的初始化數值時引入變數。

在區塊內部宣告變數也可讓您精確地控制這些變數的範圍和存留期。

有關語句的文章會說明下列 c + + 關鍵字：

:::row:::
   :::column span="":::
      [`break`](../cpp/break-statement-cpp.md)\
      [`case`](../cpp/switch-statement-cpp.md)\
      [`catch`](../cpp/try-throw-and-catch-statements-cpp.md)\
      [`continue`](../cpp/continue-statement-cpp.md)\
      [`default`](../cpp/switch-statement-cpp.md)\
      [`do`](../cpp/do-while-statement-cpp.md)
   :::column-end:::
   :::column span="":::
      [`else`](../cpp/if-else-statement-cpp.md)\
      [`__except`](../cpp/structured-exception-handling-c-cpp.md)\
      [`__finally`](../cpp/structured-exception-handling-c-cpp.md)\
      [`for`](../cpp/for-statement-cpp.md)\
      [`goto`](../cpp/goto-statement-cpp.md)
   :::column-end:::
   :::column span="":::
      [`if`](../cpp/if-else-statement-cpp.md)\
      [`__if_exists`](../cpp/if-exists-statement.md)\
      [`__if_not_exists`](../cpp/if-not-exists-statement.md)\
      [`__leave`](../c-language/try-finally-statement-c.md)\
      [`return`](../cpp/return-statement-cpp.md)
   :::column-end:::
   :::column span="":::
      [`switch`](../cpp/switch-statement-cpp.md)\
      [`throw`](../cpp/try-throw-and-catch-statements-cpp.md)\
      [`__try`](../cpp/structured-exception-handling-c-cpp.md)\
      [`try`](../cpp/try-throw-and-catch-statements-cpp.md)\
      [`while`](../cpp/while-statement-cpp.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱

[陳述式](../cpp/statements-cpp.md)
