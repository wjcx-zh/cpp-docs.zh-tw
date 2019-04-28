---
title: 編譯器錯誤 C2201
ms.date: 11/04/2016
f1_keywords:
- C2201
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
ms.openlocfilehash: b490bc32a9da0a35a726371e3b17480fcd8b0df2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368600"
---
# <a name="compiler-error-c2201"></a>編譯器錯誤 C2201

'identifier': 必須具有外部連結以便匯出/匯入

匯出的識別項是`static`。

下列範例會產生 C2286：

```
// C2201.cpp
// compile with: /c
__declspec(dllexport) static void func() {}   // C2201 func() is static
__declspec(dllexport) void func2() {}   // OK
```

## <a name="see-also"></a>另請參閱

[連結的類型](../../cpp/types-of-linkage.md)