---
title: _setmbcp
ms.date: 11/04/2016
apiname:
- _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: c1f4967baa5fda68a7df33bcd08935dca23fab16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356455"
---
# <a name="setmbcp"></a>_setmbcp

設定新的多位元組字碼頁。

## <a name="syntax"></a>語法

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>參數

*codepage*<br/>
與地區設定無關之多位元組常式的新字碼頁設定。

## <a name="return-value"></a>傳回值

如果成功設定字碼頁，則會傳回 0。 如果無效的字碼頁值提供給*字碼頁*，傳回-1 和字碼頁設定為不變。 設定組**errno**要**EINVAL**發生記憶體配置失敗。

## <a name="remarks"></a>備註

**_Setmbcp**函式會指定新的多位元組字碼頁。 根據預設，執行階段系統會自動將多位元組字碼頁設定為系統預設的 ANSI 字碼頁。 多位元組字碼頁設定會影響所有與地區設定無關的多位元組常式。 不過，它可能會指示 **_setmbcp**使用目前地區設定所定義的字碼頁 （請參閱下列清單中的資訊清單常數和相關聯行為結果）。 如需依存於地區設定字碼頁而非多位元組字碼頁的多位元組常式清單，請參閱[解譯多位元組字元序列](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。

多位元組字碼頁也會影響下列執行階段程式庫常式的多位元組字元處理︰

||||
|-|-|-|
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

此外，接收多位元組字元的所有執行階段程式庫常式*argv*或是*envp*程式做為參數的引數 (例如 **_exec**和 **_spawn**系列) 來處理這些字串會根據多位元組字碼頁。 因此，這些常式也會受到呼叫 **_setmbcp**變更多位元組字碼頁。

*字碼頁*引數可以設定為下列值之一：

- **_MB_CP_ANSI**從在程式啟動的作業系統取得使用 ANSI 字碼頁。

- **_Setmbcp**使用從先前呼叫中取得目前的地區設定字碼頁[setlocale](setlocale-wsetlocale.md)。

- **_MB_CP_OEM**從在程式啟動的作業系統取得使用 OEM 字碼頁。

- **_MB_CP_SBCS**使用單一位元組字碼頁。 當設定為的字碼頁 **_MB_CP_SBCS**，這類常式[_ismbblead](ismbblead-ismbblead-l.md)一律會傳回 false。

- 任何其他有效字碼頁值，不論值是 ANSI、OEM 或其他作業系統支援的字碼頁 (但不支援的 UTF-7 和 UTF-8 除外)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
