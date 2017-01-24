---
title: "編譯器警告 (層級 1) C4075 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4075"
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始設定式置於無法辨識的初始化區域  
  
 [\#pragma init\_seg](../../preprocessor/init-seg.md) 使用無法辨識的區段名稱。 編譯器會忽略 **pragma** 命令。  
  
 下列範例會產生 C4075：  
  
```  
// C4075.cpp // compile with: /W1 #pragma init_seg("mysegg")   // C4075 // try.. // #pragma init_seg(user) int main() { }  
```