---
title: "編譯器警告 (層級 4) C4001 | Microsoft Docs"
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
  - "C4001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4001"
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用單行註解，ANSI C 標準不支援  
  
 單行註解在 C\+\+ 中是標準的，在 C 中是非標準的。  在嚴格的 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 之下，包含單行註解的 C 檔案，由於使用了非標準的擴充，會產生 C4001。  由於在 C\+\+ 中單行註解是標準的，所以當使用 Microsoft Extensions \(\/Ze\) 編譯時，包含單行註解的 C 檔案不會產生 C4001。  
  
## 範例  
 若要停用警告，請取消註解 [\#pragma warning\(disable:4001\)](../../preprocessor/warning.md)。  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```