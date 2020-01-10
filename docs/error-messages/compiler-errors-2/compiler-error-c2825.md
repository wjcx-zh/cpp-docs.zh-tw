---
title: 編譯器錯誤 C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 6a51901477958056356a96d71adde4241d60a2ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750581"
---
# <a name="compiler-error-c2825"></a>編譯器錯誤 C2825

var：必須是類別或命名空間，後面接著 '：： '

嘗試形成限定名稱是不成功的。

例如，請確定您的程式碼不包含函式宣告，其中函數名稱的開頭為：：。

## <a name="example"></a>範例

下列範例會產生 C2825：

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
