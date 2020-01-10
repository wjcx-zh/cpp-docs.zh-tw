---
title: 編譯器錯誤 C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: fdfd2200503f80addb120117ce06f5f837d6b9f2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752011"
---
# <a name="compiler-error-c2844"></a>編譯器錯誤 C2844

' member '：不可以是介面 ' interface ' 的成員

[介面類別](../../extensions/interface-class-cpp-component-extensions.md)不能包含資料成員，除非它也是屬性。

介面中不允許屬性或成員函式以外的任何專案。 此外，不允許使用「函式」、「析構函數」和「運算子」。

下列範例會產生 C2844：

```cpp
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
