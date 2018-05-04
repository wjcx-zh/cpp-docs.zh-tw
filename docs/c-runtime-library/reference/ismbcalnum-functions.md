---
title: _ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbcalpha
- _ismbcalnum
- _ismbcdigit
- _ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha_l
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
- _ismbcdigit
- ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha
- ismbcalnum
- ismbcdigit
- ismbcalpha
- _ismbcalnum_l
- _ismbcalnum
- ismbcdigit_l
dev_langs:
- C++
helpviewer_keywords:
- ismbcalpha function
- _ismbcalnum function
- ismbcdigit_l function
- _ismbcalnum_l function
- _ismbcdigit function
- ismbcalnum function
- _ismbcalpha_l function
- ismbcdigit function
- _ismbcalpha function
- _ismbcdigit_l function
- ismbcalnum_l function
- ismbcalpha_l function
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a90fe131ff216bd9f758f3312d366e0ec29d79ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ismbcalnum-ismbcalnuml-ismbcalpha-ismbcalphal-ismbcdigit-ismbcdigitl"></a>_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l

檢查多位元組字元是否為英數字元、英文字元或數字字元。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _ismbcalnum
(
   unsigned int c
);
int _ismbcalnum_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcalpha
(
   unsigned int c
);
int _ismbcalpha_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcdigit
(
   unsigned int c
);
int _ismbcdigit_l
(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。 如果*c*< = 255，而且沒有相對應 **_ismbb**常式 (例如， **_ismbcalnum**對應至 **_ismbbalnum**)，結果會是對應的傳回值 **_ismbb**常式。

## <a name="remarks"></a>備註

這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳入的地區設定而不是目前的地區設定的地區設定相關的行為。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

|常式|測試條件|字碼頁 932 範例|
|-------------|--------------------|---------------------------|
|**_ismbcalnum**， **_ismbcalnum_l**|英數字元|傳回非零，才*c*是 ASCII 英文字母的單一位元組表示法:，請參閱範例 **_ismbcdigit**和 **_ismbcalpha**。|
|**_ismbcalpha**， **_ismbcalpha_l**|字母順序|傳回非零，才*c*是 ASCII 英文字母的單一位元組表示法： 0x41 < =*c*< = 0x5A 或 0x61 < =*c*< = 0x7A; 或片假名字母：0xA6 < =*c*< = 0xDF。|
|**_ismbcdigit**， **_ismbcdigit**|數字|傳回非零，才*c*是單一位元組表示法的 ASCII 數字： 0x30 < =*c*< = 0x39。|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_ismbcalnum**， **_ismbcalnum_l**|\<mbstring.h>|
|**_ismbcalpha**， **_ismbcalpha_l**|\<mbstring.h>|
|**_ismbcdigit**， **_ismbcdigit_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 常式](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
