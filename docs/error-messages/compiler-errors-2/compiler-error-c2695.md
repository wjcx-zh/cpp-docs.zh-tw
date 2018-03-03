---
title: "編譯器錯誤 C2695 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2695
dev_langs:
- C++
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1799e5efbf6428c5cc8f4247fb49259ef9da55ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2695"></a>編譯器錯誤 C2695
'function1': 覆寫虛擬函式只有不同於 'function2' 呼叫慣例  
  
 在衍生類別中的函式的簽章無法覆寫基底類別中的函式，並變更的呼叫慣例。  
  
 下列範例會產生 C2695:  
  
```  
// C2695.cpp  
class C {  
   virtual void __fastcall func();  
};  
  
class D : public C {  
   virtual void __clrcall func();   // C2695  
};  
```