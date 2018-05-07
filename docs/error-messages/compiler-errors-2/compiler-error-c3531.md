---
title: 編譯器錯誤 C3531 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3531
dev_langs:
- C++
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69fcacacafba752f77aacd55d5cd57b2c42b5ba9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3531"></a>編譯器錯誤 C3531
'symbol': 型別包含 'auto' 的符號必須有初始設定式  
  
 指定的變數並沒有初始設定式運算式。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  指定的初始設定式運算式，例如當您宣告變數時，會使用等號語法的簡單指派。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3531，因為變數`x1`， `y1, y2, y3`，和`z2`未初始化。  
  
```  
// C3531.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto x1;                  // C3531  
   auto y1, y2, y3;          // C3531  
   auto z1 = 1, z2, z3 = -1; // C3531  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)