---
title: "遺漏函式主體或變數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式主體"
  - "變數, 遺漏"
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 遺漏函式主體或變數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只要有了函式原型 \(Prototype\)，編譯器就可以不發生錯誤地持續執行，但連結器將無法解析位址呼叫，因為沒有保留的函式碼或變數空間。  您必須在建立該連結器必須解析的函式呼叫時，才會看到這個錯誤。  
  
## 範例  
 基本上這個函式呼叫會產生 LNK2019，因為原型會讓編譯器認為該函式存在，而連結器卻發現函式不存在。  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## 範例  
 在 C\+\+ 中，請確定為類別包含了某特定函式的實作，而不只是該類別定義中的函式原型。  如果您正在定義該標頭檔以外的類別，請務必要在函式之前包含該類別名稱 \(`Classname``::``memberfunction`\)。  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## 請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)