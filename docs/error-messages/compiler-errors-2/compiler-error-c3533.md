---
title: 編譯器錯誤 C3533 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f184f0459e7ec2251d6ff34e2ee76559fe0dea42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3533"></a>編譯器錯誤 C3533
'type': 參數不能有包含 'auto' 類型  
  
 方法或樣板參數不可以宣告`auto`關鍵字如果預設[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)作用中時，編譯器選項。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移除`auto`從參數宣告的關鍵字。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為它會宣告函式參數與`auto`關鍵字，它會使用編譯 **/zc: auto**。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為它會宣告與樣板參數`auto`關鍵字，它會使用編譯 **/zc: auto**。  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [/Zc:auto (推算變數類型)](../../build/reference/zc-auto-deduce-variable-type.md)