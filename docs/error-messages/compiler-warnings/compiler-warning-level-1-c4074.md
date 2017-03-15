---
title: "編譯器警告 (層級 1) C4074 | Microsoft Docs"
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
  - "C4074"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4074"
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4074
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始設定式置於編譯器保留的初始化區域  
  
 由 [\#pragma init\_seg](../../preprocessor/init-seg.md) 所指定的編譯器初始化區域由 Microsoft 保留。  這個區域內的程式碼會在 C 執行階段程式庫的初始化之前執行。  
  
 下列範例會產生 C4074：  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```