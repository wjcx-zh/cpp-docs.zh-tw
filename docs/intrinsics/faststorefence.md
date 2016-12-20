---
title: "__faststorefence | Microsoft Docs"
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
  - "__faststorefence_cpp"
  - "__faststorefence"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 __faststorefence"
  - "sfence 指令"
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __faststorefence
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 保證每個前一項記憶體參考 \(包括載入和儲存記憶體參考\) 在任何後續記憶體參考之前都為全域可見。  
  
## 語法  
  
```  
void __faststorefence();  
```  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__faststorefence`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 產生完整記憶體屏障指令序列，保證這個內建之前發出的載入和儲存作業，到繼續執行為止都為全域可見。  其效果與所有 x64 平台上的 `_mm_mfence` 內建很類似，但更快。  
  
 在 AMD64 平台上，這個常式所產生的指令，是比 `sfence` 指令更快的內存屏障 \(Store Fence\)。  針對時間關鍵程式碼，請在 AMD64 平台上只使用這個內建，而不是 `_mm_sfence`。  在 Intel x64 平台上，`_mm_sfence` 指令會更快。  
  
 此常式僅可作為內建常式使用。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)