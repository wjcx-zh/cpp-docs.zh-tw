---
title: "編譯器錯誤 C3540 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3befc331c4f43f4efd4e5039258e0faddae97db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3540"></a>編譯器錯誤 C3540
'type': sizeof 無法套用至包含 'auto' 的類型  
  
 [Sizeof](../../cpp/sizeof-operator.md)運算子不能套用至指定的類型，因為它包含`auto`規範。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3540。  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推算變數類型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 運算子](../../cpp/sizeof-operator.md)