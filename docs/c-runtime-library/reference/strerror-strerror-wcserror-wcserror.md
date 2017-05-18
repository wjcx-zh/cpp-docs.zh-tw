---
title: "strerror、_strerror、_wcserror、__wcserror | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
dev_langs:
- C++
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
caps.latest.revision: 21
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
ms.openlocfilehash: 3c79a2502fd9e52ff5e05e600c4d1a1e8e3761c8
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror、_strerror、_wcserror、__wcserror
取得系統錯誤訊息字串 (`strerror`、`_wcserror`)，或是將使用者提供的錯誤訊息字串格式化 (`_strerror`、`__wcserror`)。 這些函式已有更安全的版本可用，請參閱 [strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *strerror(  
   int errnum   
);  
char *_strerror(  
   const char *strErrMsg   
);  
wchar_t * _wcserror(  
   int errnum   
);  
wchar_t * __wcserror(  
   const wchar_t *strErrMsg   
);  
```  
  
#### <a name="parameters"></a>參數  
 `errnum`  
 錯誤號碼。  
  
 `strErrMsg`  
 使用者提供的訊息。  
  
## <a name="return-value"></a>傳回值  
 所有這些函式會傳回錯誤訊息字串的指標。 後續呼叫可能會複寫此字串。  
  
## <a name="remarks"></a>備註  
 `strerror` 函式會將 `errnum` 對應至錯誤訊息字串，並傳回字串的指標。 `strerror` 或 `_strerror` 實際上都不會列印訊息：因此，您必須呼叫 [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) 之類的輸出函式：  
  
```  
if (( _access( "datafile",2 )) == -1 )  
   fprintf( stderr, _strerror(NULL) );  
```  
  
 若 `strErrMsg` 傳遞為 `NULL`，則 `_strerror` 會針對上一次產生錯誤的程式庫呼叫，傳回包含系統錯誤訊息之字串的指標。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 若 `strErrMsg` 不等於 `NULL`，則 `_strerror` 會針對上一次產生錯誤的程式庫呼叫，傳回包含 (依順序) 您的字串訊息、冒號、空格、系統錯誤訊息之字串的指標，以及一個新行字元。 您的字串訊息最多可以是 94 個字元長度。  
  
 `_strerror` 的實際的錯誤號碼是儲存在變數 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中。 若要產生準確的結果，請在程式庫常式傳回錯誤時立即呼叫 `_strerror`。 否則，後續呼叫 `strerror` 或 `_strerror` 就可能會覆寫 `errno` 值。  
  
 `_wcserror` 和 `__wcserror` 分別是寬字元版本的 `strerror` 和 `_strerror`。  
  
 `_strerror`、`_wcserror` 和 `__wcserror` 不屬於 ANSI 定義，它們是 Microsoft 擴充功能，而且我們建議不要在需要可攜式程式碼時使用它們。 請針對 ANSI 相容性改用 `strerror`。  
  
 若要取得錯誤字串，建議使用 `strerror` 或 `_wcserror`，而不是遭取代的巨集 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 和 [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 以及遭取代的內部函式 `__sys_errlist` 和 `__sys_nerr`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcserror`|`strerror`|`strerror`|`_wcserror`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`strerror`|\<string.h>|  
|`_strerror`|\<string.h>|  
|`_wcserror`, `__wcserror`|\<string.h>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [perror](../../c-runtime-library/reference/perror-wperror.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、_wperror](../../c-runtime-library/reference/perror-wperror.md)
