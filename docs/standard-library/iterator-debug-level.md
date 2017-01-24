---
title: "_ITERATOR_DEBUG_LEVEL | Microsoft Docs"
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
  - "_ITERATOR_DEBUG_LEVEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ITERATOR_DEBUG_LEVEL"
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: 6
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ITERATOR_DEBUG_LEVEL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_ITERATOR_DEBUG_LEVEL` \(IDL\) 巨集取代和合併 [\_SECURE\_SCL](../standard-library/secure-scl.md) \(SCL\) 和 [\_HAS\_ITERATOR\_DEBUGGING](../standard-library/has-iterator-debugging.md) \(隱藏\) 巨集的功能。  
  
## 巨集值  
 下表摘要說明 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 巨集的值，而最後這些值如何由 `_ITERATOR_DEBUG_LEVEL` 巨集取代。  
  
 下列章節描述 SCL 和隱藏的巨集的可能值。  
  
 SCL\=0  
 停用已檢查的 Iterator。  
  
 SCL\=1  
 啟用已檢查的 Iterator。  
  
 HID\=0  
 停用 Iterator 偵錯組建。  
  
 HID\=1  
 啟用 Iterator 偵錯組建。  HID 在發行的組建中無法啟用。  
  
 下表描述 IDL 巨集值如何代替 SCL 和隱藏巨集的值。  
  
|編輯模式|新的巨集|舊巨集|說明|  
|----------|----------|---------|--------|  
|**偵錯**||||  
||IDL\=0|SCL\=0， HID\=0|停用已檢查的 Iterator 和 Iterator 停用偵錯。|  
||IDL\=1|SCL\=1， HID\=0|啟用已檢查的 Iterator 和停用 Iterator 偵錯。|  
||IDL\=2 \(預設值\)|SCL\= \(不應用\)， HID\=1|根據預設，啟用 Iterator 偵錯;已檢查的 Iterator 不相關。|  
|**Release**||||  
||IDL\=0 \(預設值\)|SCL\=0|根據預設，會停用已檢查的 Iterator。|  
||IDL\=1|SCL\=1|啟用已檢查的 Iterator;Iterator 偵錯並不相關。|  
  
## 備註  
 在發行模式，因此，如果您指定 IDL\=2.，錯誤發出。  
  
 因為 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 巨集支援類似的功能，使用的巨集和巨集值在特定情況的使用者通常不確定的。  若要解決這個問題，建議您只使用 `_ITERATOR_DEBUG_LEVEL` 巨集。  
  
## 請參閱  
 [安全程式庫：C\+\+ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)