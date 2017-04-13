---
title: "編譯器警告 （層級 3） C4373 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 36d4491f8a621f1ee97de9682faf94a26a89fa70
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4373"></a>編譯器警告 (層級 3) C4373
'%$S': 虛擬函式覆寫 '%$pS'，當參數差異只在 const/volatile 限定詞不同時，舊版本的編譯器不會覆寫  
  
 您的應用程式包含覆寫基底類別中的虛擬方法之衍生類別中的方法，並且覆寫方法中的參數只因[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)限定詞的虛擬方法的參數。 這表示編譯器必須將函式參考繫結至基底或衍生類別中的方法。  
  
 版本的編譯器之前[!INCLUDE[cpp_orcas_long](../../cpp/includes/cpp_orcas_long_md.md)]將函數繫結至基底類別中的方法，然後發出一則警告訊息。 後續版本的編譯器會忽略 `const` 或 `volatile` 限定詞，並將函式繫結至衍生類別中的方法，然後發出警告 `C4373`。 後者的行為符合 C++ 標準。  
  
## <a name="example"></a>範例  
 下列程式碼範例會產生警告 C4373：  
  
```  
// c4373.cpp  
// compile with: /c /W3  
#include <stdio.h>  
struct Base  
{  
    virtual void f(int i) {  
        printf("base\n");  
    }  
};  
struct Derived : Base  
{  
    void f(const int i) {  // C4373  
        printf("derived\n");  
    }  
};  
void main()  
{  
    Derived d;  
    Base* p = &d;  
    p->f(1);  
}  
```  
  
```Output  
derived  
```
