---
title: 編譯器錯誤 C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: f3f82549cf5d9230adfee7e83248e92f8e93e769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301340"
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

如果您嘗試將指派從資料流，也會發生 C2249C++標準程式庫至另一個資料流。  下列範例會產生 C2249。

```
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```