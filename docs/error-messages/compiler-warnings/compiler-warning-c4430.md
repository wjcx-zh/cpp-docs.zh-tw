---
title: "編譯器警告 C4430 | Microsoft Docs"
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
  - "C4430"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4430"
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4430
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遺漏類型規範 \- 假設為 int。請注意：C\+\+ 不支援 default\-int  
  
 這項錯誤可能是因為針對 Visual C\+\+ 2005 完成之編譯器一致性工作的結果所產生：所有宣告都必須明確指定型別；已不再假設為 int。  
  
 C4430 永遠視同錯誤。您可以使用 `#pragma warning` 或 **\/wd** 關閉這個警告。如需詳細資訊，請參閱 [warning](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../../build/reference/compiler-option-warning-level.md)。  
  
## 範例  
 下列範例會產生 C4430。  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```