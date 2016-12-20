---
title: "編譯器警告 (層級 3) C4101 | Microsoft Docs"
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
  - "C4101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4101"
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4101
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' ：未參考的區域變數  
  
 這個區域變數從未被使用。  這個警告會發生在明顯情況下：  
  
```  
// C4101a.cpp  
// compile with: /W3  
int main() {  
int i;   // C4101  
}  
```  
  
 然而，這個警告也會發生在透過某類別 \(Class\) 執行個體，呼叫一個 **static** 成員函式 \(Member Function\) 時：  
  
```  
// C4101b.cpp  
// compile with:  /W3  
struct S {  
   static int func()  
   {  
      return 1;  
   }  
};  
  
int main() {  
   S si;   // C4101, si is never used  
   int y = si.func();  
   return y;  
}  
```  
  
 在這種情況下，編譯器會使用 `si` 的資訊，存取 **static** 函式，但並不需要該類別的執行個體，就能呼叫 **static** 函式；所以才會產生這個警告。  若要解決這個警告，您可以：  
  
-   加入一個建構函式 \(Constructor\)，使編譯器在此建構函式中使用 `si` 的執行個體呼叫 `func`。  
  
-   移除 `func` 定義中的 **static** 關鍵字。  
  
-   明確呼叫 **static** 函式: `int y = S::func();`。