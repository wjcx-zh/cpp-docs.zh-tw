---
title: "編譯器錯誤 C3533 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3533
dev_langs: C++
helpviewer_keywords: C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7bcd9c710ac5cdd50b966a72291918459d984be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3533"></a>編譯器錯誤 C3533
'type': 參數不能有包含 'auto' 類型  
  
 方法或樣板參數不可以宣告`auto`關鍵字如果預設[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)作用中時，編譯器選項。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移除`auto`從參數宣告的關鍵字。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為它會宣告函式參數與`auto`關鍵字，它會使用編譯**/zc: auto**。  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為它會宣告與樣板參數`auto`關鍵字，它會使用編譯**/zc: auto**。  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [/Zc: auto （推算變數類型）](../../build/reference/zc-auto-deduce-variable-type.md)