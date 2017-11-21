---
title: _lfind | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lfind
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
- lfind
- _lfind
dev_langs: C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f883aa9f17c8272335a91ebf333e050888be8257
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="lfind"></a>_lfind
執行所指定索引鍵的線性搜尋。 已有比這個函式更安全的版本；請參閱 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### <a name="parameters"></a>參數  
 `key`  
 要搜尋的物件。  
  
 `base`  
 搜尋資料基底的指標。  
  
 `num`  
 陣列元素數目。  
  
 `width`  
 陣列元素的寬度。  
  
 `compare`  
 比較常式的指標。 第一個參數是搜尋索引鍵的指標。 第二個參數是要與索引鍵比較之陣列元素的指標。  
  
## <a name="return-value"></a>傳回值  
 如果找到索引鍵，`_lfind` 將指標傳回至 `base` 與 `key` 相符的陣列元素。 如果找不到索引鍵，`_lfind` 會傳回 `NULL`。  
  
## <a name="remarks"></a>備註  
 `_lfind` 函式會在 `num` 個元素的陣列中執行線性搜尋，尋找 `key` 值，每個元素 `width` 個位元組。 不同於 `bsearch`，`_lfind` 不需要排序陣列。 `base` 引數是要搜尋之陣列基底的指標。 `compare` 引數是使用者所提供之常式的指標，該常式比較兩個陣列元素，然後傳回一個指定其關聯性的值。 `_lfind` 在搜尋時會呼叫`compare` 常式一或多次，每次呼叫會將指標傳遞至兩個陣列元素。 `compare` 常式必須比較項目，然後傳回非零 (表示項目不同) 或 0 (表示項目完全相同)。  
  
 這個函式會驗證它的參數。 如果 `compare`、`key` 或 `num` 是 `NULL`，或者如果 `base`是 NULL 且 *`num` 為非零值，或如果 `width` 小於零，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行， `errno` 會設為 `EINVAL` ，且此函式會傳回 `NULL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_lfind`|\<search.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_lfind.c  
// This program uses _lfind to search a string array  
// for an occurrence of "hello".  
  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
  
int main( )  
{  
   char *arr[] = {"Hi", "Hello", "Bye"};  
   int n = sizeof(arr) / sizeof(char*);  
   char **result;  
   char *key = "hello";  
  
   result = (char **)_lfind( &key, arr,   
                      &n, sizeof(char *), compare );  
  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "hello not found!\n" );  
}  
```  
  
```Output  
Hello found  
```  
  
## <a name="see-also"></a>另請參閱  
 [搜尋和排序](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)