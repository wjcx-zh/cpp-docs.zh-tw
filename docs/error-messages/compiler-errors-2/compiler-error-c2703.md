---
title: 編譯器錯誤 C2703
description: 描述 Microsoft C/c + + 編譯器錯誤 C2703。
ms.date: 08/24/2020
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 4d5b5ccad1cd15c1a107c81423e2372e14165776
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898599"
---
# <a name="compiler-error-c2703"></a>編譯器錯誤 C2703

> 不合法的 `__leave` 語句

## <a name="remarks"></a>備註

**`__leave`** 語句必須在 **`__try`** 區塊內。

## <a name="example"></a>範例

下列範例會產生 C2703：

```cpp
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```

## <a name="see-also"></a>請參閱

[`__leave`關鍵字](../../cpp/try-except-statement.md#__leave)\
[`try-except` 聲明](../../cpp/try-except-statement.md)\
[`try-finally` 聲明](../../cpp/try-finally-statement.md)
