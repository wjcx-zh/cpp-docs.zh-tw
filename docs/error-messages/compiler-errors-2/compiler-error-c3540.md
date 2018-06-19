---
title: 編譯器錯誤 C3540 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27bae73d387612be41d8462bf0e5e0d82516ba1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256040"
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
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推算變數類型）](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 運算子](../../cpp/sizeof-operator.md)