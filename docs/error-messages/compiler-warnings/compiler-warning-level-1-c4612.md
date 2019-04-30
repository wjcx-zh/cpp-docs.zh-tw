---
title: 編譯器警告 (層級 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406362"
---
# <a name="compiler-warning-level-1-c4612"></a>編譯器警告 (層級 1) C4612

> Include 檔檔名錯誤

## <a name="remarks"></a>備註

當檔案名稱不正確或遺漏時， **#pragma include_alias** 會發生這個錯誤。

引數 **#pragma include_alias**陳述式可以使用引號形式 (「*檔名*") 或角括弧形式 (\<*filename*>)，但兩者都必須使用相同的格式。

## <a name="example"></a>範例

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```