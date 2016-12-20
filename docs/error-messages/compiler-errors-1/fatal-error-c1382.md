---
title: "嚴重錯誤 C1382 | Microsoft Docs"
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
  - "C1382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1382"
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已經重建 PCH 檔案 'file'，因為已產生 'obj'。請重建這個物件  
  
 使用 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 時，編譯器偵測到 .pch 檔的日期比指向它的 CIL .obj 更新。  CIL .obj 檔中的資訊已逾期。  請重建該目的檔。  
  
 如果以 **\/Yc** 進行編譯，但同時也傳遞多個原始程式檔給編譯器，可能也會發生 C1382。若要解決這個問題，傳遞多個原始程式檔給編譯器時，請不要使用 **\/Yc**。如需詳細資訊，請參閱[\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md)。