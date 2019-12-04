---
title: 編譯器錯誤 C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741400"
---
# <a name="compiler-error-c3836"></a>編譯器錯誤 C3836

不允許靜態的函式具有成員初始化運算式清單

Managed 類別不能有也具有成員初始化清單的靜態函式。 通用語言執行平臺會呼叫靜態類別的函式來進行類別初始化，初始化靜態資料成員。

## <a name="example"></a>範例

下列範例會產生 C3836：

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
