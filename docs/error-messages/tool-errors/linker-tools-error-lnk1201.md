---
title: "連結器工具錯誤 LNK1201 | Microsoft Docs"
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
  - "LNK1201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1201"
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫入程式資料庫 'filename' 時發生錯誤；請檢查磁碟空間是否足夠、路徑是否正確或是否有足夠的權限  
  
 LINK 無法寫入輸出檔的程式資料庫 \(PDB\)。  
  
### 若要修正，請檢查下列可能原因  
  
1.  檔案損毀。  請刪除 PDB 檔並重新連結。  
  
2.  磁碟空間不足，無法寫入檔案。  
  
3.  磁碟無法使用，可能是網路問題所造成。  
  
4.  偵錯工具正作用於您要連結的程式。  
  
5.  堆積空間不足。如需詳細資訊，請參閱 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)。