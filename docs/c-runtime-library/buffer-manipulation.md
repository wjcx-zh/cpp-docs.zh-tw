---
title: "緩衝區操作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "緩衝區"
  - "緩衝區, 管理常式"
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 緩衝區操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這些常式與記憶體使用區域是以位元組為基礎的。  
  
### 緩衝處理常式  
  
|常式|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[\_memccpy](../c-runtime-library/reference/memccpy.md)|複製某個緩衝區的字元至另一個直到特定字元數已複製|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)， [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[memchr、wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|傳回指向第一次出現的指標，在字元內指定的數字，在緩衝區中的指定字元|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[memcmp、wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|從兩個緩衝區比較指定的字元數|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)， [System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy\_s、wmemcpy\_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|從緩衝區複製指定的字元數到另一個|[System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)， [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)|  
|[\_memicmp、\_memicmp\_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|從兩個緩衝區比較指定的字元數，不考慮大小寫|[System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)， [System::String::Equals](https://msdn.microsoft.com/en-us/library/system.string.equals.aspx)|  
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove\_s、wmemmove\_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|從緩衝區複製指定的字元數到另一個|[\<caps:sentence id\="tgt21" sentenceid\="3833f84fafc5c85a0cac972319a7142c" class\="tgtSentence"\>System::Buffer::BlockCopy\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)|  
|[memset、wmemset](../c-runtime-library/reference/memset-wmemset.md)|使用指定的字元至初始化指定數目的位元組緩衝區|[\<caps:sentence id\="tgt23" sentenceid\="b681ccb0db940e3c31a14bf4b7e7aaf8" class\="tgtSentence"\>System::Buffer::SetByte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.buffer.setbyte.aspx)|  
|[\_swab](../c-runtime-library/reference/swab.md)|交換位元組資料並在指定的位置儲存它們。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
 當來源和目標區域重疊，只有 `memmove` 保證正確複製完整來源。  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)