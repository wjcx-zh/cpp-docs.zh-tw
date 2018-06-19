---
title: 編譯器錯誤 C3481 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77fc0f542a74cb077e59882e31dd1acb10c7b7e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250481"
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
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)