---
title: "BSCMAKE 錯誤 BK1509 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1509"
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# BSCMAKE 錯誤 BK1509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆積空間不足  
  
 BSCMAKE 執行時造成記憶體不足，包括虛擬記憶體在內。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  釋放部分磁碟空間。  
  
2.  增加交換檔 \(Swap File\) 的大小。  
  
3.  增加 Windows 交換檔的大小。  
  
4.  透過使用 \/Ei 或 \/Es 減少部分輸入檔案，或使用 \/Em 減少巨集主體來降低 BSCMAKE 所需的記憶體。