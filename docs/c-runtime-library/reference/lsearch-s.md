---
title: _lsearch_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _lsearch_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch_s
- lsearch_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a680c990ec91edf225057ea729fd3343a57610d4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="lsearchs"></a>_lsearch_s
執行值的線性搜尋。 這是 [_lsearch](../../c-runtime-library/reference/lsearch.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 要搜尋之陣列的基底指標。  
  
 `num`  
 項目數。  
  
 `size`  
 每個陣列元素的大小 (以位元組為單位)。  
  
 `compare`  
 比較常式的指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。  
  
 `context`  
 可能在比較函式中存取之物件的指標。  
  
## <a name="return-value"></a>傳回值  
 如果找到 `key`，`_lsearch_s` 會傳回與 `key` 相符之 `base` 處之陣列元素的指標。 如果找不到 `key`，`_lsearch_s` 會傳回陣列結尾新增項目的指標。  
  
 若傳遞了無效的參數到此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，且此函式會傳回 `NULL`。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|!= 0|any|`EINVAL`|  
|any|any|any|any|零|`EINVAL`|  
|any|any|`NULL`|an|任何|`EINVAL`|  
  
## <a name="remarks"></a>備註  
 `_lsearch_s` 函式會在 `num` 個元素的陣列中執行線性搜尋，尋找 `key` 值，每個元素 `width` 個位元組。 不同於 `bsearch_s`，`_lsearch_s` 不需要排序陣列。 如果找不到 `key`，則 `_lsearch_s` 會將其新增至陣列結尾，並遞增 `num`。  
  
 `compare` 函式是使用者所提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。 `compare` 函式也會採用內容指標作為第一個引數。 `_lsearch_s` 在搜尋時會呼叫 `compare` 一或多次，每次呼叫會將指標傳遞至兩個陣列元素。 `compare` 必須比較元素，然後傳回非零 (表示元素不同) 或 0 (表示元素完全相同)。  
  
 `context` 指標適用於搜尋的資料結構是物件的一部分，且 `compare` 函式需要存取物件成員的情況。 例如，`compare` 函式中的程式碼可以將 void 指標轉換成適當的物件類型，並存取該物件的成員。 新增 `context` 指標，會使 `_lsearch_s` 更安全，因為可以使用額外的內容以避免與使用靜態變數以將資料提供給 `compare` 函式的相關重新進入錯誤。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_lsearch_s`|\<search.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)