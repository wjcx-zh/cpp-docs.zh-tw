---
title: "編譯器警告 (層級 4) C4431 | Microsoft Docs"
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
  - "C4431"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4431"
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4431
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遺漏類型規範 \- 假設為 int。注意: C 已不再支援 default\-int  
  
 對 Visual C\+\+ 2005 完成編譯器一致性處理的結果可能會產生這項錯誤：Visual C\+\+ 不再預設為將不具型別識別項建立為 int。  識別項的型別必須明確地加以指定。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 範例  
 下列範例會產生 C4431。  
  
```  
// C4431.c  
// compile with: /c /W4  
#pragma warning(default:4431)  
i;   // C4431  
int i;   // OK  
```