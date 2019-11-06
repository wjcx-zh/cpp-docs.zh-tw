---
title: _cgets_s、_cgetws_s
ms.date: 11/04/2016
api_name:
- _cgetws_s
- _cgets_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cgets_s
- cgets_s
- cgetws_s
- _cgetws_s
helpviewer_keywords:
- strings [C++], getting from console
- console, getting strings from
- _cgets_s function
- cget_s function
- _cgetws_s function
- cgetws_s function
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
ms.openlocfilehash: be2acefcf907ca9b908fa7f439b6e245a5e103d8
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624774"
---
# <a name="_cgets_s-_cgetws_s"></a>_cgets_s、_cgetws_s

從主控台取得字元字串。 這些版本的 [_cgets 和 _cgetws](../../c-runtime-library/cgets-cgetws.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

|*buffer*|*numberOfElements*|*pSizeRead*|Return|*緩衝區*的內容|
|--------------|------------------------|-----------------|------------|--------------------------|
|**NULL**|任何|任何|**EINVAL**|N/A|
|非**Null**|零|任何|**EINVAL**|未修改|
|非**Null**|任何|**NULL**|**EINVAL**|零長度字串|

## <a name="remarks"></a>備註

**_cgets_s**和 **_cgetws_s**從主控台讀取字串，並將字串（包含 null 結束字元）複製到*緩衝區*。 **_cgetws_s**是函式的寬字元版本;除了字元大小以外，這兩個函式的行為完全相同。 要讀取的字串大小上限會以*numberOfElements*參數的形式傳入。 這個大小應該包含結束的 null 之額外字元。 讀取的實際字元數目會放在*pSizeRead*中。

如果在作業期間或在驗證參數時發生錯誤，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行， **errno**會設為**EINVAL** ，並會傳回**EINVAL** 。

在 C++ 中，樣板多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以自動將較舊且較不安全的函式取代成其較新且較安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函式的 debug 程式庫版本會先以0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cgetts_s**|**_cgets_s**|**_cgets_s**|**_cgetws_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cgets_s**|\<conio.h>|
|**_cgetws_s**|\<conio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>請參閱

[主控台和連接埠 I/O ](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
