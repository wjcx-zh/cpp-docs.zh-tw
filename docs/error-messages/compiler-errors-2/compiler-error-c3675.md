---
title: 編譯器錯誤 C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 6772572d29765370d6cdbf52ed8470ff2f3f054e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758069"
---
# <a name="compiler-error-c3675"></a>編譯器錯誤 C3675

' function '：已保留，因為已定義 ' property '

當您宣告簡單屬性時，編譯器會產生 get 和 set 存取子方法，而這些名稱會出現在程式的範圍內。  編譯器產生的名稱是藉由在屬性名稱前面加上 get_ 和 set_ 來形成。  因此，您無法使用與編譯器所產生之存取子相同的名稱來宣告函式。

如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md) 。

## <a name="example"></a>範例

下列範例會產生 C3675。

```cpp
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```
