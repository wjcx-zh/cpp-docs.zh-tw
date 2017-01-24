---
title: "編譯器錯誤 C2599 | Microsoft Docs"
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
  - "C2599"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2599"
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2599
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'enum' : 不允許列舉型別的向前宣告  
  
 編譯器不再支援 Managed 列舉的向前宣告。  
  
 在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，不允許列舉型別的向前宣告。  
  
 下列範例會產生 C2599：  
  
```  
// C2599.cpp  
// compile with: /clr /c  
enum class Status;   // C2599  
  
enum class Status2 { stop2, hold2, go2};   
  
ref struct MyStruct {  
   // Delete the following line to resolve.  
   Status m_status;  
  
   Status2 m_status2;   // OK  
};  
  
enum class Status { stop, hold, go };  
```