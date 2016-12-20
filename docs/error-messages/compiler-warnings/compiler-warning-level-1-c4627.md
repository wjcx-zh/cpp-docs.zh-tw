---
title: "編譯器警告 (層級 1) C4627 | Microsoft Docs"
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
  - "C4627"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4627"
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4627
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<識別項\>': 尋找先行編譯標頭使用時略過  
  
 搜尋使用先行編譯標頭檔的位置時，編譯器遇到 *\<識別項\>* Include 檔的 `#include` 指示詞。 編譯器會忽略 `#include` 指示詞，但如果先行編譯標頭檔尚未包含 *\<識別項\>* Include 檔，就會發出警告 **C4627**。  
  
## 請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)