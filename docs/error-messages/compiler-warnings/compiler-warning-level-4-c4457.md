---
title: "編譯器警告 （層級 4） C4457 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
caps.latest.revision: 0
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 4977ade625e3f4af5f01364b865d2c2f41ebe80a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

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

