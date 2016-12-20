---
title: "vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vfprintf_l"
  - "vfprintf"
  - "vfwprintf"
  - "_vfwprintf_l"
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
apitype: "DLLExport"
f1_keywords: 
  - "vfwprintf"
  - "_vftprintf"
  - "vfprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vfwprintf_l 函式"
  - "_vftprintf 函式"
  - "vfprintf 函式"
  - "_vftprintf_l 函式"
  - "vfprintf_l 函式"
  - "vftprintf_l 函式"
  - "vfwprintf_l 函式"
  - "vftprintf 函式"
  - "vfwprintf 函式"
  - "_vfprintf_l 函式"
  - "格式化的文字 [C++]"
ms.assetid: 4443be50-cedf-40b2-b3e2-ff2b3af3b666
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用引數清單的指標，寫入格式化輸出。 更安全的版本，這些函式存在;請參閱 [vfprintf_s、 _vfprintf_s_l、 vfwprintf_s、 _vfwprintf_s_l](../../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)。  
  
## <a name="syntax"></a>語法  
  
```  
int vfprintf(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vfwprintf(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_l(  
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
 `format`  
 格式規格。  
  
 `argptr`  
 引數清單的指標。  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="return-value"></a>傳回值  
 `vfprintf` 和 `vfwprintf` 傳回寫入的字元數目，輸出錯誤發生時，不包括結束的 null 字元或負數值。 如果 `stream` 或 `format` 為 null 指標、 無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 若允許繼續執行，函式會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
 如需這些和其他錯誤碼的資訊，請參閱 [_doserrno，errno，_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 這些函式會採用的指標引數清單，然後格式化並寫入至指定的資料 `stream`。  
  
 `vfwprintf` 是寬字元版本的 `vfprintf`; 兩個函式的 ANSI 模式開啟資料流時，如果相同行為。 `vfprintf` 目前不支援輸出成 UNICODE 資料流。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。 如需詳細資訊，請參閱 [避免緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftprintf`|`vfprintf`|`vfprintf`|`vfwprintf`|  
|`_vftprintf_l`|`_vfprintf_l`|`_vfprintf_l`|`_vfwprintf_l`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|----------------------|  
|`vfprintf`, _`vfprintf_l`|\<stdio.h> 及 \<stdarg.h>|\<varargs.h>*|  
|`vfwprintf`, _`vfwprintf_l`|\<stdio.h> 或 \<wchar.h> 及 \<stdarg.h>|\<varargs.h>*|  
  
 \* 所需的 UNIX V 相容性。  
  
 其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md) 簡介 > 中。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱 [平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、 _fprintf_l、 fwprintf、 _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、 _printf_l、 wprintf、 _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、 _sprintf_l、 swprintf、 _swprintf_l、 \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg、 va_copy、 va_end、 va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)