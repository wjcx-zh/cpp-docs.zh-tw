---
title: 編譯器錯誤 C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: ac396fe5fa3505311f5a45ebb49dae283e35248c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741407"
---
# <a name="compiler-error-c2249"></a>編譯器錯誤 C2249

' member '：沒有可存取的路徑可存取在虛擬基底 ' class ' 中宣告的成員

`member`繼承自非公用 **`virtual`** 基類或結構。

## <a name="examples"></a>範例

下列範例會產生 C2249。

```cpp
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

如果您嘗試將資料流程從 c + + 標準程式庫指派給另一個資料流程，也可能會發生 C2249。  下列範例會產生 C2249。

```cpp
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```
