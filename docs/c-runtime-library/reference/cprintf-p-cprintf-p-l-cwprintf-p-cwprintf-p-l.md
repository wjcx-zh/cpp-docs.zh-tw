---
title: "_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _cprintf_p_l
- _cwprintf_p_l
- _cwprintf_p
- _cprintf_p
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
apitype: DLLExport
f1_keywords:
- cprintf_p
- cwprintf_p
- tcprintf_p
- _cwprintf_p_l
- _cprintf_p
- csprintf_p_l
- _cprintf_p_l
- _cwprintf_p
- _tcprintf_p
- cprintf_p_l
dev_langs:
- C++
helpviewer_keywords:
- _cwprintf_p_l function
- cwprintf_p function
- tcprintf_p_l function
- cprintf_p_l function
- _tcprintf_p function
- _tcprintf_p_l function
- _cprintf_p function
- _cprintf_p_l function
- cwprintf_p_l function
- _cwprintf_p function
- tcprintf_p function
- cprintf_p function
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 347ebcc3194d74909e1d829c8c48d55fef1f0cee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cprintfp-cprintfpl-cwprintfp-cwprintfpl"></a>_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l
這會格式化並列印到主控台，且支援格式字串中的位置參數。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>語法  
  
```  
int _cprintf_p(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_p_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_p(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_p_l(  
   const wchar * format,  
   locale_t locale [,  
   argument] ...  
);  
```  
  
#### <a name="parameters"></a>參數  
 `format`  
 格式控制字串。  
  
 `argument`  
 選擇性參數。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 列印的字元數，或是當發生錯誤時為負值。  
  
## <a name="remarks"></a>備註  
 這些函式會使用 `_putch` 和 `_putwch` 函式來輸出字元，直接格式化並列印一系列的字元和值到主控台中。 每個 `argument` (如果有的話) 是根據 `format`中的對應格式規格進行轉換和輸出。 此格式具有與 [printf_p](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) 函式的 `format` 參數相同的形式和功能。 `_cprintf_p` 和 `cprintf_s` 之間的差異在於 `_cprintf_p` 支援位置參數，可讓您指定格式字串中使用引數的順序。 如需詳細資訊，請參閱 [printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 不同於`fprintf_p`， `printf_p`，和`sprintf_p`函式，兩者都不`_cprintf_p`也`_cwprintf_p`換行字元轉譯為歸位字元-換 (CR-LF) 組合輸出時。 一項重要的差異在於 `_cwprintf_p` 會在 Windows NT 中使用時顯示 Unicode 字元。 不同於 `_cprintf_p`，`_cwprintf_p` 會使用目前的主控台地區設定。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定參數，而不使用目前的地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
 並且，如同 `_cprintf_s` 和 `_cwprintf_s`，它們會驗證輸入的指標和格式字串。 如果 `format` 或 `argument` 為 `NULL`，或此格式字串包含無效格式化字元，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，這些函式會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcprintf_p`|`_cprintf_p`|`_cprintf_p`|`_cwprintf_p`|  
|`_tcprintf_p_l`|`_cprintf_p_l`|`_cprintf_p_l`|`_cwprintf_p_l`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_cprintf_p`、`_cprintf_p_l`|\<conio.h>|  
|`_cwprintf_p`、`_cwprintf_p_l`|\<conio.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_cprintf_p.c  
// This program displays some variables to the console  
// using the _cprintf_p function.  
  
#include <conio.h>  
  
int main( void )  
{  
    int         i = -16,  
                h = 29;  
    unsigned    u = 62511;  
    char        c = 'A';  
    char        s[] = "Test";  
  
    // Note that console output does not translate  
    // \n as standard output does. Use \r\n instead.  
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",   
                h, i, u, c, s );  
}  
```  
  
```Output  
-16  001d  62511  A Test  
```  
  
## <a name="see-also"></a>請參閱  
 [主控台和連接埠 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)   
 [_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)   
 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)