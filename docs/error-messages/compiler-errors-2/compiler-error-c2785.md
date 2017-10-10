---
title: "編譯器錯誤 C2785 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a545935e06d958502fb3b97cb8969f92172ca6b6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2785"></a>編譯器錯誤 C2785
'declaration1' 和 'declaration2' 的傳回類型不同  
  
 函式樣板的特製化的傳回型別不同於主要函式樣板的傳回型別。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查所有樣板的特製化函式的一致性。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2785:  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```
