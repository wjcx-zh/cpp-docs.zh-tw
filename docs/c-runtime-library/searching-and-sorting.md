---
title: "搜尋和排序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "資料 [CRT], 搜尋"
  - "搜尋 [C++]"
  - "搜尋 [C++], CRT search 函式"
  - "排序資料"
ms.assetid: 15e984f0-e155-46f5-8542-51c458792f54
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 搜尋和排序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列函式搜尋和排序。  
  
### 搜尋和排序函式  
  
|功能|搜尋或排序|.NET Framework 對等用法|  
|--------|-----------|-------------------------|  
|[bsearch](../c-runtime-library/reference/bsearch.md)|二元搜尋|[\<caps:sentence id\="tgt8" sentenceid\="07fe7161f1b3ff07a50d0fdb13bc8ade" class\="tgtSentence"\>System::Collections::ArrayList::BinarySearch\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.binarysearch.aspx)|  
|[bsearch\_s](../c-runtime-library/reference/bsearch-s.md)|`bsearch`更安全的版本。|[\<caps:sentence id\="tgt10" sentenceid\="07fe7161f1b3ff07a50d0fdb13bc8ade" class\="tgtSentence"\>System::Collections::ArrayList::BinarySearch\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.binarysearch.aspx)|  
|[\_lfind](../c-runtime-library/reference/lfind.md)|指定值的線性搜尋|[\<caps:sentence id\="tgt13" sentenceid\="2b0a5c761626afecd7137a4eab4525f0" class\="tgtSentence"\>System::Collections::ArrayList::Contains\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)|  
|[\_lfind\_s](../c-runtime-library/reference/lfind-s.md)|`_lfind`更安全的版本。|[\<caps:sentence id\="tgt15" sentenceid\="2b0a5c761626afecd7137a4eab4525f0" class\="tgtSentence"\>System::Collections::ArrayList::Contains\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.contains.aspx)|  
|[\_lsearch](../c-runtime-library/reference/lsearch.md)|指定值的線性搜尋，如果找不到，加至陣列|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_lsearch\_s](../c-runtime-library/reference/lsearch-s.md)|`_lsearch`更安全的版本。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[qsort](../c-runtime-library/reference/qsort.md)|快速分類|[\<caps:sentence id\="tgt27" sentenceid\="f0305a177c6971f2c3c37537da538229" class\="tgtSentence"\>System::Collections::ArrayList::Sort\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)|  
|[qsort\_s](../c-runtime-library/reference/qsort-s.md)|`qsort`更安全的版本。|[\<caps:sentence id\="tgt29" sentenceid\="f0305a177c6971f2c3c37537da538229" class\="tgtSentence"\>System::Collections::ArrayList::Sort\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)