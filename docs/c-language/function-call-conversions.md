---
title: 函式呼叫轉換
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: e4e84c9d4e1f25a56c0bcabcec99e5e75fcaa321
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229671"
---
# <a name="function-call-conversions"></a>函式呼叫轉換

在函式呼叫的引數上執行的類型轉換取決於函式原型 (向前宣告) 是否存在，以及所呼叫之函式宣告的引數類型。

如果函式原型存在並且包含宣告的引數類型，則編譯器會執行類型檢查 (請參閱[函式](../c-language/functions-c.md))。

如果函式原型不存在，則只會在函式呼叫中的引數上執行一般算術轉換。 這些轉換會單獨在呼叫中的各個引數上執行。 這表示 **`float`** 值會轉換成， **`double`** **`char`** 或 **`short`** 值會轉換成， **`int`** 而 **`unsigned char`** 或 **`unsigned short`** 會轉換成 **`unsigned int`** 。

## <a name="see-also"></a>另請參閱

[類型轉換](../c-language/type-conversions-c.md)
