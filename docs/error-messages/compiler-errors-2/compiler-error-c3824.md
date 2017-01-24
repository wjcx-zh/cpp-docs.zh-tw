---
title: "編譯器錯誤 C3824 | Microsoft Docs"
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
  - "C3824"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3824"
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3824
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member': 這個型別不可出現在這種內容中 \(函式參數、傳回型別或靜態成員\)  
  
 Pin 指標不可為函式參數、傳回型別，也不能宣告為 `static`。  
  
 下列範例會產生 C3824：  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  
  
 **Managed Extensions for C\+\+**  
  
 以 `__pin` 關鍵字宣告的區域指標不可以宣告為 `static`，也不可以為內部指標。  
  
 下列範例會產生 C3824：  
  
```  
// C3824b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
  
__gc struct A {};  
  
void func() {  
   static A __pin* a;   // C3824  
   A __pin* b;   // OK  
}  
```