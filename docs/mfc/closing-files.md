---
title: "關閉檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案 [C++], 關閉"
  - "MFC [C++], 檔案作業"
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 關閉檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

照例在 I\/O 作業，，一旦完成與檔案，您必須先將它關閉。  
  
#### 若要關閉檔案  
  
1.  使用 **Close** 成員函式。  這個函式會關閉檔案系統檔案，並視需要清除緩衝區。  
  
 如果您指派了框架的 [C 檔案](../mfc/reference/cfile-class.md) 物件 \(如 [開啟檔案](../mfc/opening-files.md)中所顯示的範例中\)，物件會自動關閉並終結時超出範圍。  請注意刪除 `CFile` 物件不會刪除檔案系統的實體檔案。  
  
## 請參閱  
 [檔案](../mfc/files-in-mfc.md)