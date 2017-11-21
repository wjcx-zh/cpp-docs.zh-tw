---
title: "編譯器錯誤 C2975 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2975
dev_langs: C++
helpviewer_keywords: C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65644cc13629481941ffdd8676e51311c665f106
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-error-c2975"></a>編譯器錯誤 C2975

> '*引數*': 無效的樣板引數'*類型*'，必須是編譯時期常數運算式

樣板引數不符合樣板宣告中。常數運算式應該在角括號內會出現。 變數不允許作為範本實質引數。 請檢查樣板定義，以找出正確的類型。

## <a name="example"></a>範例

下列範例會產生 C2975，並也會顯示正確的使用方式：

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

也會發生 C2975 當您使用 #95; &#95;資料行 &#95; #95;為編譯時期常數與[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)。 一個解決方式是使用編譯[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)而不是**/ZI**。

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```