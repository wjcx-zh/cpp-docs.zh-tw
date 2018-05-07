---
title: 編譯器錯誤 C3161 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d7aff3eb41c03f5be774704922340ac54126fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3161"></a>編譯器錯誤 C3161
'interface': 巢狀類別、 結構、 等位或介面中的介面是不合法;巢狀介面類別、 結構或等位中的不合法  
  
 [__Interface](../../cpp/interface.md)只可以出現在全域範圍或命名空間內。 類別、 結構或等位不能出現在介面中。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3161。  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```