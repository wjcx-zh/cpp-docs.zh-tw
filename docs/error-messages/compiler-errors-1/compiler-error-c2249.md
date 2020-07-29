---
title: 編譯器錯誤 C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: f50cb27a239e794b87a15920a36e96529bd6a466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212796"
---
# <a name="compiler-error-c2249"></a>編譯器錯誤 C2249

' member '：無法存取虛擬基底 ' class ' 中宣告的成員的路徑

`member`繼承自非公用的 **`virtual`** 基類或結構。

## <a name="example"></a>範例

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

## <a name="example"></a>範例

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
