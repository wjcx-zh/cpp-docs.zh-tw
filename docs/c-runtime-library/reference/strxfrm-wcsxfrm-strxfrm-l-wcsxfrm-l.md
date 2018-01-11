---
title: "strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs: C++
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc61e1f1dee03d0604b4a7fab97dc4236c1f705c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l
根據地區設定特定資訊轉換字串。  
  
## <a name="syntax"></a>語法  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `strDest`  
 目的字串。  
  
 `strSource`  
 來源字串。  
  
 `count`  
 要置於的字元數目上限`strDest`。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 傳回已轉換字串的長度，不計入結束的 Null 字元。 如果傳回值大於或等於 `count`，則無法預測 `strDest` 的內容。 發生錯誤時，每個函式會設定 `errno`，並傳回 `INT_MAX`。 對於無效的字元，`errno` 會設定為 `EILSEQ`。  
  
## <a name="remarks"></a>備註  
 `strxfrm` 函式將由 `strSource` 指向的字串轉換成新的定序格式，其儲存在 `strDest`。 轉換並放入結果字串的字元數不會超過 `count` 個字元，包括 Null 字元。 轉換是使用地區設定的 `LC_COLLATE` 分類設定進行。 如需 `LC_COLLATE` 的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 `strxfrm` 會針對與其地區設定相關的行為使用目前的地區設定；`_strxfrm_l` 與其相同，只不過它會使用傳入的地區設定，而不是目前的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 轉換之後，對兩個已轉換字串呼叫 `strcmp`，會產生與呼叫套用至原始兩個字串的 `strcoll` 完全相同的結果。 如同 `strcoll` 和 `stricoll`，`strxfrm` 會自動適當地處理多位元組字元字串。  
  
 `wcsxfrm` 是寬字元版本的 `strxfrm`；`wcsxfrm` 的字串引數是寬字元指標。 對於 `wcsxfrm`，在字串轉換之後，對兩個已轉換字串呼叫 `wcscmp`，會產生與呼叫套用至原始兩個字串的 `wcscoll` 完全相同的結果。 否則，`wcsxfrm` 和 `strxfrm` 的行為即會相同。 `wcsxfrm` 會針對與其地區設定相關的行為使用目前的地區設定；`_wcsxfrm_l` 使用傳入的地區設定，而不是目前的地區設定。  
  
 這些函式會驗證它們的參數。 如果 `strSource` 是 Null 指標，或 `strDest`是 Null 指標 (除非計數為零)，或是如果 `count` 大於 `INT_MAX`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `INT_MAX`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 在 "C" 地區設定中，字元集 (ASCII 字元集) 的字元順序與字元的詞典編纂順序相同。 不過，其他地區設定中，字元集的字元順序可能與詞典編纂字元順序不同。 比方說，在某些歐洲地區設定中，字元 'a' （值 0x61） 前面的字元 ' （& s)\#x00E4;'（值 0xE4） 中的字元集，但字元 'ä' 前面的字元 'a' 辭典編纂順序。  
  
 在字元集和詞典編纂字元順序不同的地區設定，請對原始字串使用 `strxfrm`，然後對產生的字串使用 `strcmp`，以產生根據目前地區設定之 `LC_COLLATE` 分類設定的詞典編纂字串比較。 如此，若要依詞典編纂順序比較上述地區設定中的兩個字串，請對原始字串使用 `strxfrm`，然後對產生的字串使用 `strcmp`。 或者，您可以對原始字串使用 `strcoll` 而不是 `strcmp`。  
  
 `strxfrm` 基本上是包裝函式，用 `LCMAP_SORTKEY` 來包裝 [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700)。  
  
 下列運算式的值，是用來儲存來源字串之 `strxfrm` 轉換所需的陣列大小︰  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 僅限 "C" 地區設定，`strxfrm` 相當於下列︰  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strxfrm`|\<string.h>|  
|`wcsxfrm`|\<string.h> 或 \<wchar.h>|  
|`_strxfrm_l`|\<string.h>|  
|`_wcsxfrm_l`|\<string.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)