---
title: _lsearch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lsearch
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
- _lsearch
- lsearch
dev_langs:
- C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 86dd9925775d50a8e1c79f677f3e5b1d9ad3ae37
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="lsearch"></a>_lsearch
執行值的線性搜尋；如果找不到，則新增至清單結尾。 這個函式已有更安全的版本可用；請參閱 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 要搜尋之陣列的基底指標。  
  
 `num`  
 項目數。  
  
 `width`  
 每個陣列元素的寬度。  
  
 `compare`  
 比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。  
  
## <a name="return-value"></a>傳回值  
 如果找到索引鍵，`_lsearch` 會傳回與 `key` 相符的 `base` 處之陣列元素的指標。 如果找不到索引鍵，`_lsearch` 會傳回陣列結尾新增項目的指標。  
  
## <a name="remarks"></a>備註  
 `_lsearch` 函式會在 `num` 個元素的陣列中執行線性搜尋，尋找 `key` 值，每個元素 `width` 個位元組。 不同於 `bsearch`，`_lsearch` 不需要排序陣列。 如果找不到 `key`，`_lsearch` 會將其新增至陣列結尾，並遞增 `num`。  
  
 `compare` 引數是使用者所提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。 `_lsearch` 在搜尋時會呼叫`compare` 常式一或多次，每次呼叫會將指標傳遞至兩個陣列元素。 `compare` 必須比較元素，然後傳回非零 (表示元素不同) 或 0 (表示元素完全相同)。  
  
 這個函式會驗證它的參數。 如果 `compare`、`key` 或 `num` 是 `NULL`，或者如果 `base`是 NULL 且 *`num` 為非零值，或如果 `width` 小於零，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行， `errno` 會設為 `EINVAL` ，且此函式會傳回 `NULL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_lsearch`|\<search.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_lsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main(void)  
{  
   char * wordlist[4] = { "hello", "thanks", "bye" };  
                            // leave room to grow...  
   int n = 3;  
   char **result;  
   char *key = "extra";  
   int i;  
  
   printf( "wordlist before _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
  
   result = (char **)_lsearch( &key, wordlist,   
                      &n, sizeof(char *), compare );  
  
   printf( "wordlist after _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
}  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
```  
  
```Output  
wordlist before _lsearch: hello thanks bye  
wordlist after _lsearch: hello thanks bye extra  
```  
  
## <a name="see-also"></a>另請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)
