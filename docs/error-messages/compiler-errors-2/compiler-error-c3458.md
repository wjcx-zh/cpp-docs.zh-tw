---
title: 編譯器錯誤 C3458
ms.date: 11/04/2016
f1_keywords:
- C3458
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
ms.openlocfilehash: 98f3dc8ec880a2d134da4cc1438841744b8d9a94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756652"
---
# <a name="compiler-error-c3458"></a>編譯器錯誤 C3458

'attribute1': 屬性 'attribute2 ' 已對 'construct' 指定，而這兩個屬性互斥

針對相同的建構指定了兩個互斥的屬性。

## <a name="example"></a>範例

下列範例會產生 C3458

```cpp
// C3458.cpp
// compile with: /clr /c
[System::Reflection::DefaultMember("Chars")]
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458
   property char default[int] {
      char get(int index);
      void set(int index, char c);
   }
};
```
