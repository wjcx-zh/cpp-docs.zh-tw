---
title: "編譯器錯誤 C3532 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3532
dev_langs: C++
helpviewer_keywords: C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b85baf8e2e53885b07758772d3328f70fe93b35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3532"></a>編譯器錯誤 C3532
'type': 'auto' 的使用方式不正確  
  
 指定的類型不可以宣告與`auto`關鍵字。 例如，您不能使用`auto`關鍵字來宣告陣列或方法的傳回型別。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定初始化運算式會產生有效的型別。  
  
2.  請不要宣告陣列或方法的傳回型別。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3532 因為`auto`關鍵字不能宣告方法的傳回型別。  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3532 因為`auto`關鍵字不能宣告陣列。  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)