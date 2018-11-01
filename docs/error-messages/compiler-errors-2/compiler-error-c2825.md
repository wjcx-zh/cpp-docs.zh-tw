---
title: 編譯器錯誤 C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 1e2f8e8cd38b90a698994743609892896ef0d1a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625871"
---
# <a name="compiler-error-c2825"></a>編譯器錯誤 C2825

var： 必須是類別或命名空間時，後面接著 ':: '

失敗的嘗試已對形成限定的名稱。

例如，請確定您的程式碼不包含函式宣告，其中函式名稱開頭為::。

## <a name="example"></a>範例

下列範例會產生 C2825:

```
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```