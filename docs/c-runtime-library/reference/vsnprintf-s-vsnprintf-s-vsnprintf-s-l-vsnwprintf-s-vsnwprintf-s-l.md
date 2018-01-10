---
title: "vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
dev_langs: C++
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8df40232ae7a6a92343e86fc00db5f4f0e571ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l
使用引數清單的指標，寫入格式化輸出。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l](../../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
int vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   va_list argptr   
);  
int _vsnprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vsnwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vsnwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int _vsnprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int _vsnwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 輸出的儲存位置。  
  
 `sizeOfBuffer`  
 輸出的 `buffer` 大小如字元計數。  
  
 `count`  
 要寫入的字元數目上限 (不包括終止的 Null) 或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 `format`  
 格式規格。  
  
 `argptr`  
 引數清單的指標。  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## <a name="return-value"></a>傳回值  
 `vsnprintf_s`、`_vsnprintf_s` 和 `_vsnwprintf_s` 會傳回寫入的字元數，但不包含終止的 Null，或在發生輸出錯誤時傳回負值。 `vsnprintf_s` 等同於 `_vsnprintf_s` `vsnprintf_s` 包含在內，以符合 ANSI 規範。 `_vnsprintf` 保留以提供回溯相容性。  
  
 如果儲存資料和終止 Null 所需的儲存體超過 `sizeOfBuffer`，則叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述，除非 `count` 是[_TRUNCATE](../../c-runtime-library/truncate.md)，在此情況下會儘可能寫入適合 `buffer` 的字串並傳回 -1。 如果在無效的參數處理常式之後繼續執行，則這些函式會將 `buffer` 設定為空字串、將 `errno` 設定為 `ERANGE`，並傳回 -1。  
  
 如果 `buffer` 或 `format` 為 `NULL` 指標，或者 `count` 小於或等於零，則會叫用無效的參數處理常式。 如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` ，並傳回 -1。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`Condition`|Return|`errno`|  
|-----------------|------------|-------------|  
|`buffer` 是 `NULL`|-1|`EINVAL`|  
|`format` 是 `NULL`|-1|`EINVAL`|  
|`count` <= 0|-1|`EINVAL`|  
|`sizeOfBuffer` 太小 (且 `count` != `_TRUNCATE`)|-1 (且 `buffer` 設為空字串)|`ERANGE`|  
  
## <a name="remarks"></a>備註  
 所有這些函式都會接受引數清單的指標，然後格式化指定的資料，並將其最多 `count` 個字元寫入 `buffer` 指向的記憶體，再附加終止的 Null。  
  
 如果 `count` 為 [_TRUNCATE](../../c-runtime-library/truncate.md)，則這些函式會盡量將字串放入 `buffer`，同時保留終止 Null 的空間。 如果整個字串 (含終止 Null) 可放入 `buffer`，則這些函式會傳回寫入的字元數 (不含終止 Null)；否則，這些函式會傳回 -1 表示發生截斷。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
> [!NOTE]
>  為確保障終止的 Null 有足夠空間，`count` 絕對要小於緩衝區長度，或使用 `_TRUNCATE`。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vsntprintf_s`|`_vsnprintf_s`|`_vsnprintf_s`|`_vsnwprintf_s`|  
|`_vsntprintf_s_l`|`_vsnprintf_s_l`|`_vsnprintf_s_l`|`_vsnwprintf_s_l`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|----------------------|  
|`vsnprintf_s`|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|  
|`_vsnprintf_s`, `_vsnprintf_s_l`|\<stdio.h> 和 \<stdarg.h>|\<varargs.h>*|  
|`_vsnwprintf_s`, `_vsnwprintf_s_l`|\<stdio.h> 或 \<wchar.h>，以及 \<stdarg.h>|\<varargs.h>*|  
  
 \* UNIX V 相容性的必要項目。  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_vsnprintf_s.cpp  
#include <stdio.h>  
#include <wtypes.h>  
  
void FormatOutput(LPCSTR formatstring, ...)   
{  
   int nSize = 0;  
   char buff[10];  
   memset(buff, 0, sizeof(buff));  
   va_list args;  
   va_start(args, formatstring);  
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);  
   printf("nSize: %d, buff: %s\n", nSize, buff); 
   va_end(args); 
}  
  
int main() {  
   FormatOutput("%s %s", "Hi", "there");  
   FormatOutput("%s %s", "Hi", "there!");  
   FormatOutput("%s %s", "Hi", "there!!");  
}  
```  
  
```Output  
nSize: 8, buff: Hi there  
nSize: 9, buff: Hi there!  
nSize: -1, buff: Hi there!  
```  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、_fprintf_l、fwprintf、_fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、_printf_l、wprintf、_wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg、va_copy、va_end、va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)