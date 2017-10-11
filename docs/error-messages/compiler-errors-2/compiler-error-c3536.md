---
title: "編譯器錯誤 C3536 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 90db065c9a16e72a396bd1c1ae54bb99cdb97153
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3536"></a>編譯器錯誤 C3536
'symbol': 無法在初始化之前使用。  
  
 在初始化之前，無法使用指定的符號。 實際上，這表示不能使用變數來初始化它自己。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  無法初始化本身的變數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3536，因為每個變數會初始化與其本身。  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)
