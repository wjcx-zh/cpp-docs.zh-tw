---
title: Null 陳述式
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
ms.openlocfilehash: 167a1e579c15fd59da1979efd9aa979184318115
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177803"
---
# <a name="null-statement"></a>Null 陳述式

「Null 語句」是運算式語句，其中遺漏*運算式*。 它對於呼叫陳述式，但是不進行運算式評估的語言語法相當實用。 它是由一個分號所構成。

null 陳述式通常用來做為反覆項目陳述式中的預留位置，或做為在複合陳述式或函式的結尾放置一個標籤的陳述式。

下列程式碼片段顯示如何將某個字串複製到另一個字串，以及合併 null 陳述式：

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>另請參閱

[運算陳述式](../cpp/expression-statement.md)
