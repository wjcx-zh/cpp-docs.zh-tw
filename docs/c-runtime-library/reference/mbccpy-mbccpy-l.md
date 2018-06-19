---
title: _mbccpy、_mbccpy_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbccpy
- _mbccpy_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs:
- C++
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d79ab8362eaa911b7a4aa936d6351aa29f610fa8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403166"
---
# <a name="mbccpy-mbccpyl"></a>_mbccpy、_mbccpy_l

將多位元組字元從某個字串複製到另一個字串。 這些函式已有更安全的版本可用，請參閱 [_mbccpy_s、_mbccpy_s_l](mbccpy-s-mbccpy-s-l.md)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
void _mbccpy(
   unsigned char *dest,
   const unsigned char *src
);
void _mbccpy_l(
   unsigned char *dest,
   const unsigned char *src,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*目的地*複製目的地。

*src*複製多位元組字元。

*地區設定*来使用的地區設定。

## <a name="remarks"></a>備註

**_Mbccpy**函式會複製一個多位元組字元從*src*至*目的地*。

這個函式會驗證它的參數。 如果 **_mbccpy**傳遞的 null 指標*目的地*或*src*、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 若要繼續，允許執行**errno**設**EINVAL**。

**_mbccpy**針對任何地區設定相關行為使用目前的地區設定。 **_mbccpy_l**等同於 **_mbccpy**不同之處在於 **_mbccpy_l**會針對任何地區設定相關行為傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**安全性提示**：使用以 Null 結束的字串。 以 Null 結束的字串不得超過目的緩衝區的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 緩衝區滿溢問題是系統攻擊常見的方法，會造成權限無故提高。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy**|巨集或內嵌函式的對應|**_mbccpy**|巨集或內嵌函式的對應|
|**_tccpy_l**|N/A|**_mbccpy_l**|N/A|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbccpy**|\<mbctype.h>|
|**_mbccpy_l**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
