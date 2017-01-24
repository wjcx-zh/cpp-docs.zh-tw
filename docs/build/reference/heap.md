---
title: "/HEAP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "堆積配置，設定堆積大小"
  - "HEAP editbin 選項"
  - "-HEAP editbin 選項"
  - "/HEAP editbin 選項"
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HEAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以位元組設定堆積的大小。  這個選項只適用於可執行檔。  
  
```  
  
/HEAP:  
reserve[,commit]  
  
```  
  
## 備註  
 `reserve` 引數會指定虛擬記憶體中初始堆積配置 \(Heap Allocation\) 的總計。  預設的堆積大小為 1 MB。  [EDITBIN 參考](../../build/reference/editbin-reference.md)會將指定的值進位至最接近 4 的倍數個位元組。  
  
 選擇性 `commit` 引數是隨作業系統的解讀而異。  在 Windows 作業系統上，並指定初始的實體記憶體的配置和數量其他記憶體配置時必須展開堆積。  認可的虛擬記憶體會在分頁檔中保留空間。  當應用程式需要更多堆積空間，但會增加記憶體需求且可能增加應用程式啟動期間時，較高的 `commit` 值允許系統經常配置記憶體較少。  `commit` 值必須小於或等於 `reserve` 值。  
  
 指定 `reserve` 值和 `commit` 值以十進位數或 C 語言十六進位或八進位標記法。  例如， 1 MB 的值都可以指定十進位為 1048576 ，在十六位元則為 0x100000 ，或者八進位為 04000000。  
  
## 請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)