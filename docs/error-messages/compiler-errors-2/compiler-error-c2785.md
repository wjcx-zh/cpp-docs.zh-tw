---
title: 編譯器錯誤 C2785 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc0ca6235e0fd4bdd22330e807464e96280ae461
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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