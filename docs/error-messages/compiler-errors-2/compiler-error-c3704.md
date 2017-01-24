---
title: "編譯器錯誤 C3704 | Microsoft Docs"
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
  - "C3704"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3704"
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3704
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : vararg 方法無法引發事件  
  
 您嘗試在 Vararg 方法上使用 [\_\_event](../../cpp/event.md)。  若要修正此錯誤，請以 `fireEvent(int i, ...)` 呼叫取代 `fireEvent(int i)` 呼叫，如下列程式碼範例所示。  
  
 下列範例會產生 C3704：  
  
```  
// C3704.cpp  
[ event_source(native) ]  
class CEventSrc {  
   public:  
      __event void fireEvent(int i, ...);   // C3704  
      // try the following line instead:  
      // __event void fireEvent(int i);  
};  
  
int main() {  
}  
```