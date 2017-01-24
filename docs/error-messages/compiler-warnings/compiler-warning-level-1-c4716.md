---
title: "編譯器警告 (層級 1) C4716 | Microsoft Docs"
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
  - "C4716"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4716"
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4716
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 必須傳回值  
  
 提供的函式未傳回值。  
  
 只有具有 void 傳回型別的函式，才能在不指定傳回值的情況下使用傳回命令。  
  
 當此函式被呼叫時會傳回未定義的值。  
  
 此警告會自動提升為錯誤。  如果您要修改此行為，請使用 [\#pragma warning](../../preprocessor/warning.md)。  
  
 下列範例會產生 C4716：  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```