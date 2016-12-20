---
title: "編譯器錯誤 C3628 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3628"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3628"
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3628
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'base class'：managed 或 WinRT 類別僅支援公用繼承  
  
 嘗試使用 managed 或 WinRT 類別做為[私用](../../cpp/private-cpp.md)或[受保護](../../cpp/protected-cpp.md)基底類別。  managed 或 WinRT 類別只可以當做具有[公用](../../cpp/public-cpp.md)存取權的基底類別。  
  
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
  
 下列範例會產生 C3628，並顯示如何修正此問題：  
  
```  
// C3628b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__gc class B {  
};  
  
__gc class D : B {   // C3628, private is the default access level  
  
// The following line resolves the error.  
// __gc class D : public B {  
};  
  
int main() {  
}  
```