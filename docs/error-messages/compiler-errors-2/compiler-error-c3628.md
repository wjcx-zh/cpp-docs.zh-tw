---
title: "編譯器錯誤 C3628 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 131b2829991d0d8c40b64c903afd45b485b9ba55
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3628"></a>編譯器錯誤 C3628
'base class': managed 或 WinRTclasses 僅支援公用繼承  
  
嘗試使用 managed 或 WinRT 類別做為[私人](../../cpp/private-cpp.md)或[保護](../../cpp/protected-cpp.md)基底類別。 Managed 或 WinRT 類別只可用來當作基底類別具有[公用](../../cpp/public-cpp.md)存取。  
  
下列範例會產生 C3628，並顯示如何修正此問題：  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  

