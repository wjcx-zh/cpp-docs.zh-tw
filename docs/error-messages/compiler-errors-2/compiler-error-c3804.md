---
title: 編譯器錯誤 C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: c3c00d1d07306a9e8dc67d3f75a5cb25d8f03aee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400080"
---
# <a name="compiler-error-c3804"></a>編譯器錯誤 C3804

'property_accessor': 存取子方法的屬性必須是靜態或所有非靜態

存取子函式定義時的重要屬性，可以是靜態或執行個體，但非兩者。

如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md) 。

## <a name="example"></a>範例

下列範例會產生 C3804。

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```