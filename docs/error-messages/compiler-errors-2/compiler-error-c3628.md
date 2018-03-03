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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16e2e2a83cc5dbf52e7030e10d00c3cdfe7891d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
