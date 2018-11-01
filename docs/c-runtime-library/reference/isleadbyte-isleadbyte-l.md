---
title: isleadbyte、_isleadbyte_l
ms.date: 11/04/2016
apiname:
- _isleadbyte_l
- isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: 1a3f427e49e53bb553020da100b0e713350fab3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531885"
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte、_isleadbyte_l

判斷某個字元是否為多位元組字元的前導位元組。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

## <a name="return-value"></a>傳回值

**isleadbyte**如果引數符合測試條件或 0 則會傳回非零值。 在"C"地區設定和單一位元組字元集 (SBCS) 地區設定中， **isleadbyte**一律會傳回 0。

## <a name="remarks"></a>備註

**Isleadbyte**巨集會傳回非零值，如果其引數是多位元組字元的第一個位元組。 **isleadbyte**會產生有意義的結果的任何整數引數，介於-1 (**EOF**) 來**UCHAR_MAX** (0xFF)，內含。

預期的引數型別**isleadbyte**是**int**; 如果傳遞的帶正負號的字元，則編譯器可能會將它轉換成整數的正負號擴充，產生無法預期的結果。

使用此函式的版本 **_l**尾碼是完全相同，不同之處在於它會使用傳入的地區設定而不是目前的地區設定針對與其地區設定相關的行為。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|一律傳回 false|**_isleadbyte**|一律傳回 false|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
