---
title: 編譯器警告 （層級 4） C4456 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ca4af4e7353595dc687b77fa87acf70861bcb6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4456"></a>編譯器警告 （層級 4） C4456
  
> 宣告的 '*識別碼*' 會隱藏先前的區域宣告
  
宣告*識別碼*在區域範圍會隱藏相同名稱的前一個區域宣告的宣告。 這項警告可讓您知道要參考*識別碼*本機範圍中解析的區域宣告的版本，不先前 local，這可能或可能不到您的意圖。 若要修正此問題，我們建議您提供本機變數名稱，不會產生衝突，與其他本機名稱。  
    
## <a name="example"></a>範例
  
下列範例會產生 C4456，因為迴圈控制變數`int x`和區域變數`double x`中`member_fn`有相同的名稱。 若要修正此問題，請使用不同名稱的本機變數。  
  
```cpp  
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        } 
        x += u; // uses local double x
    }
} s;
```  
