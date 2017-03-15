---
title: "_InterlockedAddLargeStatistic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedAddLargeStatistic"
  - "_InterlockedAddLargeStatistic_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建 _InterlockedAddLargeStatistic"
  - "內建 InterlockedAddLargeStatistic"
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _InterlockedAddLargeStatistic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 執行連鎖的加法裡面第一個運算元是一個 64 位元值。  
  
## 語法  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### 參數  
 輸入 \[、 輸出\]`Addend`  
 若要加入作業的第一個運算元變數的指標。  加法的結果就會取代所指到的值。  
  
 \[in\] `Value`  
 第二個運算元中。 若要新增至第一個運算元的值。  
  
## 傳回值  
 第二個運算元的值。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建不不可部分完成，因為它已依照實施兩個不同的鎖定的指示進行。  發生於另一個執行緒在執行期間內建的不可部分完成 64 位元讀取可能會導致不一致的值，被讀取。  
  
 這個函式具有作用的讀寫的障礙。  如需詳細資訊，請參閱 [\_ReadWriteBarrier](../intrinsics/readwritebarrier.md)。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)