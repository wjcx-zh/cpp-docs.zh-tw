---
title: "編譯器錯誤 C3481 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 316bf1e6bdbe3837c744642b61f1023566fd0095
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3481"></a>編譯器錯誤 C3481
'var': 找不到 Lambda 擷取變數  
  
 編譯器找不到傳遞至 Lambda 運算式擷取清單的變數定義。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請從 Lambda 運算式的擷取清單移除變數。  
  
## <a name="example"></a>範例  
 下例會產生 C3481，因為未定義變數 `n` ：  
  
```  
// C3481.cpp  
  
int main()  
{  
   [n] {}(); // C3481  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)