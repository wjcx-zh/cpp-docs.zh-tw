---
title: 編譯器警告 （層級 4） C4457 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80eac0ade54df1626e993bfed12468b2aa34402f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4457"></a>編譯器警告 （層級 4） C4457
  
> 宣告的 '*識別碼*' 會隱藏函式參數
  
宣告*識別碼*在區域範圍會隱藏相同名稱的函式參數的宣告。 這項警告可讓您知道要參考*識別碼*本機範圍中解析的區域宣告的版本，不會使用參數，這可能或可能不到您的意圖。 若要修正此問題，我們建議您提供參數名稱與本機變數名稱沒有衝突。  
    
## <a name="example"></a>範例
  
下列範例會產生 C4457，因為參數`x`和區域變數`x`中`member_fn`有相同的名稱。 若要修正此問題，請使用不同的參數和區域變數的名稱。  
  
```cpp  
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        } 
        a += x; // uses parameter x
    }
} s;
```  
