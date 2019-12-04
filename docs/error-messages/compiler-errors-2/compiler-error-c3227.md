---
title: 編譯器錯誤 C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 460000531dba77e42379199f276c9e2e02f43a9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743415"
---
# <a name="compiler-error-c3227"></a>編譯器錯誤 C3227

' parameter '：不能使用 ' 關鍵字 ' 來配置泛型型別

若要具現化型別，則需要適當的函式。 不過，編譯器無法確保有適當的可用的函式。

您可以使用範本（而不是泛型）來解決這個錯誤，也可以使用數種方法的其中一種來建立類型的實例。

## <a name="example"></a>範例

下列範例會產生 C3227。

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
