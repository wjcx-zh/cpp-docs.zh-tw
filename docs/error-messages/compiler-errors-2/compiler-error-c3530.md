---
title: "編譯器錯誤 C3530 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0d66e76fc3e44a037f52aa6e217fae848f1338d2
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3530"></a>編譯器錯誤 C3530
'auto' 無法與任何其他類型規範結合  
  
 類型規範搭配`auto`關鍵字。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請勿使用型別規範中使用的變數宣告`auto`關鍵字。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3530，因為變數`x`宣告同時`auto`關鍵字和類型`int`，而且因為此範例會使用編譯**/zc: auto**。  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)
