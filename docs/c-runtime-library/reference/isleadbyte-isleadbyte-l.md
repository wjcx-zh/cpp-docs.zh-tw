---
title: isleadbyte、_isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 1d2202bd1ca59ee42287c398da429df132e24fcb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234077"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte、_isleadbyte_l

判斷某個字元是否為多位元組字元的前導位元組。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>參數

*c*<br/>
待測試整數。

## <a name="return-value"></a>傳回值

如果引數符合測試條件， **isleadbyte**會傳回非零值，否則會傳回0。 在 "C" 地區設定和單位元組字元集（SBCS）地區設定中， **isleadbyte**一律會傳回0。

## <a name="remarks"></a>備註

如果**isleadbyte**宏的引數是多位元組字元的第一個位元組，則會傳回非零值。 **isleadbyte**會針對任何從-1 （**EOF**）到**UCHAR_MAX** （0xff）（含）的整數引數產生有意義的結果。

**Isleadbyte**的預期引數類型為 **`int`** ; 如果傳遞了帶正負號的字元，編譯器可能會將它轉換成以符號擴充的整數，因而產生無法預期的結果。

具有 **_l**尾碼的這個函式版本是一樣的，不同之處在于它會使用傳入的地區設定，而非目前的地區設定來處理其地區設定相關的行為。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
