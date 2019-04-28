---
title: _ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l
ms.date: 11/04/2016
apiname:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
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
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
ms.openlocfilehash: 07855ec970b2bf307238982987912f1e91505e96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286828"
---
# <a name="ismbclegal-ismbclegall-ismbcsymbol-ismbcsymboll"></a>_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l

檢查多位元組字元是否為合法或符號字元。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
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

如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。 如果*c*< = 255 且有對應 **_ismbb**常式 (例如 **_ismbcalnum**對應至 **_ismbbalnum**)，結果是對應的傳回值 **_ismbb**常式。

## <a name="remarks"></a>備註

這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。

使用這些函式的版本 **_l**尾碼都相同，不同之處在於使用傳入的地區設定而不是目前的地區設定其地區設定相關行為。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

|常式傳回的值|測試條件|字碼頁 932 範例|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|有效的多位元組|第一個位元組傳回非零值，才*c*是在範圍內 0x81-0x9F 或 0xE0-0xFC，而是內範圍 0x40-0x7E 或 0x80-FC 的第二個位元組。|
|**_ismbcsymbol**|多位元組的符號|傳回非零值，才在 0x8141< < =*c*< lt;=0x81ac。|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|一律傳回 false|**_ismbclegal**|一律傳回 false。|
|**_istlegal_l**|一律傳回 false|**_ismbclegal_l**|一律傳回 false。|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_ismbclegal**， **_ismbclegal_l**|\<mbstring.h>|
|**_ismbcsymbol**， **_ismbcsymbol_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 常式](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
