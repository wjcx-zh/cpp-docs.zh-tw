---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 18712661b2bda1eaaf0c583b922ad73a781b4abc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918820"
---
# <a name="_setmbcp"></a>_setmbcp

設定新的多位元組字碼頁。

## <a name="syntax"></a>語法

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>參數

*頁*<br/>
與地區設定無關之多位元組常式的新字碼頁設定。

## <a name="return-value"></a>傳回值

如果成功設定字碼頁，則會傳回 0。 如果為字碼頁提供了不正確字碼頁*值，則*會傳回-1，而字碼頁設定則不會變更。 如果發生記憶體配置失敗，則將**errno**設定為**EINVAL** 。

## <a name="remarks"></a>備註

**_Setmbcp**函數會指定新的多位元組字碼頁。 根據預設，執行階段系統會自動將多位元組字碼頁設定為系統預設的 ANSI 字碼頁。 多位元組字碼頁設定會影響所有與地區設定無關的多位元組常式。 不過，您可以指示 **_setmbcp**使用針對目前地區設定所定義的字碼頁（請參閱下列資訊清單常數清單和相關聯的行為結果）。 如需依存於地區設定字碼頁而非多位元組字碼頁的多位元組常式清單，請參閱[解譯多位元組字元序列](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。

多位元組字碼頁也會影響下列執行階段程式庫常式的多位元組字元處理︰

||||
|-|-|-|
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

此外，所有接收多位元組字元*argv*或*envp*程式引數做為參數的執行時間程式庫常式（例如 **_exec**和 **_spawn**系列）都會根據多位元組字碼頁來處理這些字串。 因此，這些常式也會受到變更多位元組字碼頁之 **_setmbcp**的呼叫所影響。

*字碼頁*引數可以設定為下列任何值：

- **_MB_CP_ANSI**在程式啟動時，使用從作業系統取得的 ANSI 字碼頁。

- **_MB_CP_LOCALE**使用從先前的[setlocale](setlocale-wsetlocale.md)呼叫中取得的目前地區設定字碼頁。

- **_MB_CP_OEM**在程式啟動時，使用從作業系統取得的 OEM 字碼頁。

- **_MB_CP_SBCS**使用單一位元組字碼頁。 當字碼頁設定為 **_MB_CP_SBCS**時，如[_ismbblead](ismbblead-ismbblead-l.md)的常式一律會傳回 false。

- **_MB_CP_UTF8**使用 UTF-8。  當字碼頁設定為 **_MB_CP_UTF8**時，如[_ismbblead](ismbblead-ismbblead-l.md)的常式一律會傳回 false。

- 任何其他有效的字碼頁值，不論值是否為 ANSI、OEM 或其他作業系統支援的字碼頁（不支援的 UTF-7 除外）。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
