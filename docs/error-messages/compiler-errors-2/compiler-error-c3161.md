---
title: "編譯器錯誤 C3161 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4be981b2af166d85a3a83209a901f3e3e51b6246
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
