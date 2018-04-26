---
title: _vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _vscprintf
- _vscprintf_l
- _vscwprintf_l
- _vscwprintf
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
- vscprintf_l
- vscwpeintf
- _vscwprintf
- _vsctprintf
- _vscprintf
- vscwprintf_l
- vscprintf
- _vscwprintf_l
dev_langs:
- C++
helpviewer_keywords:
- vsctprintf function
- _vscprintf_l function
- _vsctprintf_l function
- _vsctprintf function
- _vscwprintf_l function
- vscwprintf_l function
- _vscprintf function
- _vscwprintf function
- vscwprintf function
- vsctprintf_l function
- formatted text [C++]
- vscprintf function
- vscprintf_l function
ms.assetid: 1bc67d3d-21d5-49c9-ac8d-69e26b16a3c3
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a8cfdd7eded5956e9e34faed53e93e0ad029361
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="vscprintf-vscprintfl-vscwprintf-vscwprintfl"></a>_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l

使用引數清單的指標傳回格式化的字串字元數。

## <a name="syntax"></a>語法

```C
int _vscprintf(
   const char *format,
   va_list argptr
);
int _vscprintf_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vscwprintf(
   const wchar_t *format,
   va_list argptr
);
int _vscwprintf_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>參數

*格式*<br/>
格式控制字串。

*argptr*<br/>
引數清單的指標。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

**_vscprintf**傳回會產生如果指向的字串引數清單的字元數已列印或傳送至檔案或使用指定的格式設定的緩衝區代碼。 傳回的值不包含終止 Null 字元。 **_vscwprintf**寬字元中執行相同的功能。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳遞而不是目前的執行緒地區設定的地區設定參數。

如果*格式*為 null 指標，無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回-1，並設定**errno**至**EINVAL**。

## <a name="remarks"></a>備註

每個*引數*（如果有的話） 會轉換中的對應格式規格根據*格式*。 此格式包含一般字元，與具有相同的形式和功能*格式*引數[printf](printf-printf-l-wprintf-wprintf-l.md)。

> [!IMPORTANT]
> 確保當*格式*是使用者定義的字串，它是 null 終止，而且有正確的數目和參數的類型。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsctprintf**|**_vscprintf**|**_vscprintf**|**_vscwprintf**|
|**_vsctprintf_l**|**_vscprintf_l**|**_vscprintf_l**|**_vscwprintf_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_vscprintf**， **_vscprintf_l**|\<stdio.h>|
|**_vscwprintf**， **_vscwprintf_l**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [vsprintf](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
