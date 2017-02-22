---
title: "堆積常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_HEAPBADPTR"
  - "_HEAPEMPTY"
  - "_HEAPBADBEGIN"
  - "_HEAPOK"
  - "_HEAPBADNODE"
  - "_HEAPEND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_HEAPBADBEGIN 常數"
  - "_HEAPBADNODE 常數"
  - "_HEAPBADPTR 常數"
  - "_HEAPEMPTY 常數"
  - "_HEAPEND 常數"
  - "_HEAPOK 常數"
  - "堆積常數"
  - "HEAPBADBEGIN 常數"
  - "HEAPBADNODE 常數"
  - "HEAPBADPTR 常數"
  - "HEAPEMPTY 常數"
  - "HEAPEND 常數"
  - "HEAPOK 常數"
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 堆積常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <malloc.h>  
  
```  
  
## 備註  
 這些常數指出堆積狀態的回傳值。  
  
|常數|意義|  
|--------|--------|  
|`_HEAPBADBEGIN`|初始標頭資訊找不到或不正確。|  
|`_HEAPBADNODE`|找到錯誤的節點，或堆積損毀。|  
|`_HEAPBADPTR`|**\_HEAPINFO** 的**\_pentry** 欄位未包含有效輸入至堆積的指標 \(僅有`_heapwalk`常式 \)。|  
|`_HEAPEMPTY`|堆積尚未初始化。|  
|`_HEAPEND`|堆積結尾成功到達 \(僅有`_heapwalk`常式 \)。|  
|`_HEAPOK`|堆積是一致的 \(僅有`_heapset` 和 `_heapchk` 常式\)。  到目前為止沒有錯誤; **\_HEAPINFO** 結構包含下個輸入 \(僅限`_heapwalk` 常式的資訊\)。|  
  
## 請參閱  
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapset](../c-runtime-library/heapset.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全域常數](../c-runtime-library/global-constants.md)