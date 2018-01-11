---
title: "wctomb_s、_wctomb_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wctomb_s_l
- wctomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs: C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3c819f62f36966363f32eb16b7af758de274d3d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="wctombs-wctombsl"></a>wctomb_s、_wctomb_s_l
將寬字元轉換為對應的多位元組字元。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pRetValue`  
 位元組數目，或表示結果的代碼。  
  
 [輸出] `mbchar`  
 多位元組字元的位址。  
  
 [輸入] `sizeInBytes`  
 `mbchar` 緩衝區的大小。  
  
 [in] `wchar`  
 寬字元。  
  
 [輸入] `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為零，失敗則為錯誤碼。  
  
 錯誤狀況  
  
|`mbchar`|`sizeInBytes`|傳回值|`pRetValue`|  
|--------------|-------------------|------------------|-----------------|  
|`NULL`|>0|`EINVAL`|未修改|  
|any|>`INT_MAX`|`EINVAL`|未修改|  
|any|太小|`EINVAL`|未修改|  
  
 如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`wctomb` 會傳回 `EINVAL`，且 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `wctomb_s` 函式會將其 `wchar` 引數轉換成對應的多位元組字元，並將結果儲存在 `mbchar`。 您可以在任何程式的任何點呼叫函式。  
  
 如果 `wctomb_s` 將寬字元轉換成多位元組字元，它會將寬字元的位元組數目 (絕不會大於 `MB_CUR_MAX`) 放入 `pRetValue` 指向的整數。 如果 `wchar` 是寬字元的 Null 字元 (L'\0')，`wctomb_s` 會用 1 填入 `pRetValue`。 如果目標指標 `mbchar` 是 NULL，則 `wctomb_s` 會將 0 放入 `pRetValue`。 如果轉換不可能在目前的地區設定， `wctomb_s` -1 會置於`pRetValue`。  
  
 `wctomb_s` 會針對與地區設定相關的資訊使用目前的地區設定，`_wctomb_s_l` 與其相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`wctomb_s`|\<stdlib.h>|  
|`_wctomb_s_l`|\<stdlib.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 此程式說明 `wctomb` 函式的行為。  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
```Output  
Convert a wide character:  
   Characters converted: 1  
   Multibyte character: a  
```  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)