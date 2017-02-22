---
title: "_lsearch_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lsearch_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_lsearch_s"
  - "lsearch_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_lsearch_s 函式"
  - "陣列 [CRT], 搜尋"
  - "索引鍵, 在陣列中尋找"
  - "線性搜尋"
  - "lsearch_s 函式"
  - "搜尋, 線性"
  - "值, 搜尋"
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _lsearch_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行線性搜尋值。  這是 [\_lsearch](../../c-runtime-library/reference/lsearch.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### 參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 要搜尋的基底陣列的指標。  
  
 `num`  
 項目數  
  
 `size`  
 每個陣列項目大小\(位元\)。  
  
 `compare`  
 要比較常式的指標。  第二個參數是指向搜尋的索引指標。  第三個參數是指向與索引鍵比較的陣列元素。  
  
 `context`  
 在比較函式可能被存取之物件的指標。  
  
## 傳回值  
 如果找到`key`，則 `_lsearch_s` 會傳回與 `key`相符的`base`陣列的項目的指標 。  如果找不到 `key` ， `_lsearch_s` 將指標傳回新加入的項目在陣列結尾。  
  
 如果傳給函式無效的參數，無效參數處理常式將被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  如果允許繼續執行，會將 `errno`  設為 `EINVAL`，並傳回`NULL` 。  如需詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 錯誤狀況  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|\!\= 0|any|`EINVAL`|  
|any|any|any|any|零|`EINVAL`|  
|any|any|`NULL`|一|any|`EINVAL`|  
  
## 備註  
 `_lsearch_s` 函式在陣列中的 `num` 項目用 `key` 執行線性搜尋，每 `width` 位元組。  不同於 `bsearch_s`， `_lsearch_s` 不需要先排序陣列。  如果找不到 `key` ，則 `_lsearch_s` 將它加入至陣列結尾並加入 `num`。  
  
 `compare`函式是指向比較兩個陣列元素和傳回指定其關聯性之值的使用者提供的常式。  `compare` 函式只接受指標到內容做為第一個引數。  在搜尋過程中，`_lsearch_s` 會呼叫 `compare` 常式一次或多次，並於每次呼叫傳遞兩個陣列元素的指標。  `compare` 必須比較項目且傳回非零 \(表示項目是不同的\) 或 0 \(表示項目中相同\)。  
  
 如果被搜尋的資料結構為物件的一部分，`context` 指標會很有用，而且 `compare` 函式需要存取物件的成員。  舉例來說，`compare` 函式的程式碼可以將 null 指標轉型為適當的物件型別，然後存取該物件的成員。  因為其他內容可以用來避免關於使用靜態變數讓 `compare` 函式可以存取資料的可重入錯誤 ，則 `context` 指標加入使 `_lsearch_s` 更安全。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lsearch_s`|\<search.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch\_s](../../c-runtime-library/reference/bsearch-s.md)   
 [\_lfind\_s](../../c-runtime-library/reference/lfind-s.md)   
 [\_lsearch](../../c-runtime-library/reference/lsearch.md)