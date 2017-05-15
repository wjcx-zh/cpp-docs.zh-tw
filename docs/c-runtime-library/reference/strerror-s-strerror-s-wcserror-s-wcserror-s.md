---
title: "strerror_s、_strerror_s、_wcserror_s、__wcserror_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
dev_langs:
- C++
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 70875568a8f77f9e4039e69dadbe9daf3c1c5e01
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s
取得系統錯誤訊息 (`strerror_s`、`_wcserror_s`)，或列印使用者提供的錯誤訊息 (`_strerror_s`、`__wcserror_s`)。 這些是 [strerror、_strerror、_wcserror、\__wcserror](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t _strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *strErrMsg   
);  
errno_t _wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t __wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *strErrMsg   
);  
template <size_t size>  
errno_t strerror_s(  
   char (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t _strerror_s(  
   char (&buffer)[size],  
   const char *strErrMsg   
); // C++ only  
template <size_t size>  
errno_t _wcserror_s(  
   wchar_t (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t __wcserror_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *strErrMsg   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 要保存錯誤字串的緩衝區。  
  
 `numberOfElements`  
 緩衝區的大小。  
  
 `errnum`  
 錯誤號碼。  
  
 `strErrMsg`  
 使用者提供的訊息。  
  
## <a name="return-value"></a>傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### <a name="error-condtions"></a>錯誤狀況  
  
|`buffer`|`numberOfElements`|`strErrMsg`|`buffer` 的內容。|  
|--------------|------------------------|-----------------|--------------------------|  
|`NULL`|any|any|N/A|  
|any|0|any|未修改|  
  
## <a name="remarks"></a>備註  
 `strerror_s` 函式會將 `errnum` 對應至錯誤訊息字串，並傳回 `buffer` 中的字串。 `_strerror_s` 不接受錯誤號碼，而是使用 `errno` 的目前值來判斷適當的訊息。 `strerror_s` 或 `_strerror_s` 實際上都不會列印訊息：因此，您必須呼叫 [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) 之類的輸出函式：  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 若 `strErrMsg` 為 `NULL`，`_strerror_s` 會針對上一次產生錯誤的程式庫呼叫，傳回 `buffer` 中包含系統錯誤訊息的字串。 錯誤訊息字串會以新行字元 ('\n') 為結尾。 若 `strErrMsg` 不等於 `NULL`，則 `_strerror_s` 會針對上一次產生錯誤的程式庫呼叫，傳回 `buffer` 中包含 (依順序) 您的字串訊息、冒號、空格、系統錯誤訊息的字串，以及一個新行字元。 您的字串訊息最多可以是 94 個字元長度。  
  
 如果錯誤訊息的長度超過 `numberOfElements` -1，這些函式會截斷錯誤訊息。 `buffer` 中所產生的字串一律會以 Null 結束。  
  
 `_strerror_s` 的實際的錯誤號碼是儲存在變數 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 中。 系統錯誤訊息是透過變數 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 來存取，這是依錯誤號碼排序的訊息陣列。 `_strerror_s` 會使用 `errno` 值作為變數 `_sys_errlist` 的索引，來存取適當的錯誤訊息。 變數 [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的值已定義為 `_sys_errlist` 陣列中的元素數目上限。 若要產生準確的結果，請在程式庫常式傳回錯誤時立即呼叫 `_strerror_s`。 否則，後續呼叫 `strerror_s` 或 `_strerror_s` 就可能會覆寫 `errno` 值。  
  
 `_wcserror_s` 和 `__wcserror_s` 分別是寬字元版本的 `strerror_s` 和 `_strerror_s`。  
  
 這些函式會驗證它們的參數。 如果緩衝區為 `NULL` 或大小參數為 0，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
 `_strerror_s``_wcserror_s`，和`__wcserror_s`不屬於 ANSI 定義，但會改為 Microsoft 擴充功能。 請勿在需要可攜性的情況下使用這些函式；如需 ANSI 相容性，請改用 `strerror_s`。  
  
 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`strerror_s`, `_strerror_s`|\<string.h>|  
|`_wcserror_s`, `__wcserror_s`|\<string.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [perror](../../c-runtime-library/reference/perror-wperror.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、_wperror](../../c-runtime-library/reference/perror-wperror.md)
