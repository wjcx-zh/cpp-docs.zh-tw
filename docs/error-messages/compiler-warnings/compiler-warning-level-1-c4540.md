---
title: "編譯器警告 (層級 1) C4540 | Microsoft Docs"
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
  - "C4540"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4540"
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4540
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dynamic\_cast 用來轉換為不可存取或模擬兩可的基底; 執行階段測試將會失敗 \('type1' 至 'type2'\)  
  
 您使用 `dynamic_cast` 將型別轉換成其他型別。  編譯器決定轉換一律失敗 \(傳回 **NULL**\)，因為無法存取基底類別 \(例如是 `private`\) 或模稜兩可 \(例如在類別階層中出現一次以上\)。  
  
 以下顯示此種警告的範例。  類別 **B** 是從類別 **A** 衍生而來。  程式是使用 `dynamic_cast`，將類別 **B** \(衍生類別\) 轉換成類別 **A**，但因為類別 **B** 是 `private` 而無法存取，所以轉換一律都會失敗。  將 **A** 的存取改為 **public**，就可以解除這項警告。  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```