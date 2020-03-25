---
title: 編譯器警告 (層級 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: f9478caef9eaba9c72dc282179100daf2d94c6d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185980"
---
# <a name="compiler-warning-level-1-c4612"></a>編譯器警告 (層級 1) C4612

> Include 檔檔名錯誤

## <a name="remarks"></a>備註

當檔案名稱不正確或遺漏時， **#pragma include_alias** 會發生這個錯誤。

**#Pragma include_alias**語句的引數可以使用引號格式（"*檔案名*"）或角括弧形式（\<*filename*>），但兩者都必須使用相同的格式。

## <a name="example"></a>範例

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```
