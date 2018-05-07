---
title: 編譯器錯誤 C3495 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7accbc422256abbd75d518acce72c522fbb67c14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3495"></a>編譯器錯誤 C3495
'var': Lambda 擷取必須有自動儲存期  
  
 您無法擷取沒有自動儲存期的變數，例如標記為 `static` 或 `extern`的變數。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請勿將 `static` 或 `extern` 變數傳遞至 Lambda 運算式的擷取清單。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3495，因為 `static` 變數 `n` 出現在 Lambda 運算式的擷取清單中：  
  
```  
// C3495.cpp  
  
int main()  
{  
   static int n = 66;  
   [&n]() { return n; }(); // C3495  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)   


