---
title: 編譯器錯誤 C3917
ms.date: 11/04/2016
f1_keywords:
- C3917
helpviewer_keywords:
- C3917
ms.assetid: a24cd0c9-262f-46e5-9488-1c01f945933d
ms.openlocfilehash: 393d1213f58ab50424093927cbc975651ce34e65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567471"
---
# <a name="compiler-error-c3917"></a>編譯器錯誤 C3917

'*屬性*': 過時的建構宣告樣式

屬性或事件定義中使用從 Visual Studio 2005 之前版本的語法。

如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

```cpp
// C3917.cpp
// compile with: /clr /c
public ref class  C {
private:
   int m_length;
public:
   C() {
      m_length = 0;
   }

   property int get_Length();   // C3917

   // The correct property definition:
   property int Length {
      int get() {
         return m_length;
      }

      void set( int i ) {
         m_length = i;
      }
   }
};
```