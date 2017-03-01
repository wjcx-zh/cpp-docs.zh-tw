---
title: "_cprintf、_cprintf_l、_cwprintf、_cwprintf_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cwprintf_l
- _cprintf_l
- _cwprintf
- _cprintf
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
- _cwprintf
- cwprintf
- tcprintf
- _tcprintf
- _cprintf
- cwprintf_l
- tcprintf_l
- _tcprintf_l
- cprintf_l
- _cprintf_l
- _cwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- _cprintf_l function
- _cwprintf_l function
- cwprintf function
- cprintf_l function
- characters, printing to console
- printing characters to console
- _tcprintf_l function
- tcprintf function
- _tcprintf function
- tcprintf_l function
- _cwprintf function
- cwprintf_l function
- _cprintf function
ms.assetid: 67ffefd4-45b3-4be0-9833-d8d26ac7c4e2
caps.latest.revision: 34
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d761621d23ab97d951199e7790e71f224394f92c
ms.lasthandoff: 02/24/2017

---
# <a name="cprintf-cprintfl-cwprintf-cwprintfl"></a>_cprintf、_cprintf_l、_cwprintf、_cwprintf_l
格式化並列印至主控台。 已有更安全的版本可用；請參閱 [_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int _cprintf(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_l(   
   const char * format,  
   locale_t locale [,  
   argument] …   
);  
int _cwprintf(  
   const wchar * format [,   
   argument] …  
);  
int _cwprintf_l(  
   const wchar * format,  
   locale_t locale [,   
   argument] …  
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
 已列印的字元數。  
  
## <a name="remarks"></a>備註  
 這些函式會使用 `_putch` 函式 (`_putwch` 用於 `_cwprintf`) 來輸出字元，直接格式化一系列的字元和值，並將其列印到主控台。 每個 `argument` (如果有的話) 是根據 `format`中的對應格式規格進行轉換和輸出。 此格式具有與 [printf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) 函式的 `format` 參數相同的形式和功能。 不同於 `fprintf`、`printf` 和 `sprintf` 函式，`_cprintf` 和 `_cwprintf` 在輸出時不會將換行字元轉譯為歸位字元-換行字元 (CR-LF) 組合。  
  
 一項重要的差異在於 `_cwprintf` 會在 Windows NT 中使用時顯示 Unicode 字元。 不同於 `_cprintf`，`_cwprintf` 會使用目前的主控台地區設定。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定參數，而不使用目前的地區設定。  
  
 `_cprintf` 驗證 `format` 參數。 如果 `format` 是 Null 指標，則此函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，則函式會傳回 -1 並將 `errno` 設定為 `EINVAL`。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcprintf`|`_cprintf`|`_cprintf`|`_cwprintf`|  
|`_tcprintf_l`|`_cprintf_l`|`_cprintf_l`|`_cwprintf_l`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_cprintf`、`_cprintf_l`|\<conio.h>|  
|`_cwprintf`, `_cwprintf_l`|\<conio.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_cprintf.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
    int         i = -16,  
                h = 29;  
    unsigned    u = 62511;  
    char        c = 'A';  
    char        s[] = "Test";  
  
    // Note that console output does not translate \n as  
    // standard output does. Use \r\n instead.  
    //  
    _cprintf( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
```Output  
-16  001d  62511  A Test  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [主控台和連接埠 I/O](../../c-runtime-library/console-and-port-i-o.md)   
 [_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)   
 [_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
