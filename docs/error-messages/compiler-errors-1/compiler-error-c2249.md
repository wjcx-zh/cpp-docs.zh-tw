---
title: 編譯器錯誤 C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: f3f82549cf5d9230adfee7e83248e92f8e93e769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555622"
---
# <a name="compiler-error-c2249"></a>編譯器錯誤 C2249

'member': 沒有可存取的路徑來存取成員宣告虛擬基底 'class' 中

`member`繼承自非公用`virtual`基底類別或結構。

## <a name="example"></a>範例

下列範例會產生 C2249。

```
// C2249.cpp
class A {
private:
   void privFunc( void ) {};
public:
   void pubFunc( void ) {};
};

class B : virtual public A {} b;

int main() {
   b.privFunc();    // C2249, private member of A
   b.pubFunc();    // OK
}
```

## <a name="example"></a>範例

如果您嘗試將指派從 c + + 標準程式庫的資料流到另一個資料流，也會發生 C2249。  下列範例會產生 C2249。

```
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```