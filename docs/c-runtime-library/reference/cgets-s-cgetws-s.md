---
title: _cgets_s、_cgetws_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _cgetws_s
- _cgets_s
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb384629be21a8233d69a1f25a9cf469f7a0413
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="cgetss-cgetwss"></a>_cgets_s、_cgetws_s

從主控台取得字元字串。 這些版本的 [_cgets 和 _cgetws](../../c-runtime-library/cgets-cgetws.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _cgets_s(
   char *buffer,
   size_t numberOfElements,
   size_t *pSizeRead
);
errno_t _cgetws_s(
   wchar_t *buffer
   size_t numberOfElements,
   size_t *pSizeRead
);
template <size_t size>
errno_t _cgets_s(
   char (&buffer)[size],
   size_t *pSizeRead
); // C++ only
template <size_t size>
errno_t _cgetws_s(
   wchar_t (&buffer)[size],
   size_t *pSizeRead
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
資料的儲存位置。

*numberOfElements*<br/>
緩衝區的大小，以單一位元組或寬字元為單位，也是要讀取的字元數上限。

*pSizeRead*<br/>
實際讀取的字元數。

## <a name="return-value"></a>傳回值

如果成功則傳回值為零；否則，如果發生失敗則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*buffer*|*numberOfElements*|*pSizeRead*|Return|內容*緩衝區*|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|任何|任何|**EINVAL**|N/A|
|不**NULL**|零|任何|**EINVAL**|未修改|
|不**NULL**|任何|**NULL**|**EINVAL**|零長度字串|

## <a name="remarks"></a>備註

**_cgets_s**和 **_cgetws_s**從主控台讀取字串，並將字串 （包括 null 結束字元） 複製到*緩衝區*。 **_cgetws_s**是寬字元版本的函式; 除了字元大小之外，這兩個函數的行為相同。 要讀取之字串的大小上限會傳入做為*numberOfElements*參數。 這個大小應該包含結束的 null 之額外字元。 實際讀取的字元數會置於*pSizeRead*。

如果在作業期間或在驗證參數時發生錯誤，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 若要繼續，允許執行**errno**設**EINVAL**和**EINVAL**傳回。

在 C++ 中，樣板多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以自動將較舊且較不安全的函式取代成其較新且較安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[主控台和連接埠 I/O ](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
