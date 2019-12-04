---
title: 編譯器錯誤 C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761812"
---
# <a name="compiler-error-c3161"></a>編譯器錯誤 C3161

' interface '：在介面中嵌套類別、結構、等位或介面不合法;在類別、結構或等位中嵌套介面不合法

[__Interface](../../cpp/interface.md)只能出現在全域範圍或命名空間中。 類別、結構或等位不能出現在介面中。

## <a name="example"></a>範例

下列範例會產生 C3161。

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
