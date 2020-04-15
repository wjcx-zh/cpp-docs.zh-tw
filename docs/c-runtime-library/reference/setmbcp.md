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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337596"
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

*代碼頁*<br/>
與地區設定無關之多位元組常式的新字碼頁設定。

## <a name="return-value"></a>傳回值

如果成功設定字碼頁，則會傳回 0。 如果為*代碼頁*提供了無效的代碼頁值,則返回 -1,並且代碼頁設置保持不變。 如果發生記憶體分配失敗,則將**errno**設置到**EINVAL。**

## <a name="remarks"></a>備註

**_setmbcp**函數指定一個新的多位元組碼頁。 根據預設，執行階段系統會自動將多位元組字碼頁設定為系統預設的 ANSI 字碼頁。 多位元組字碼頁設定會影響所有與地區設定無關的多位元組常式。 但是,可以指示 **_setmbcp**使用為當前區域設置定義的代碼頁(請參閱以下清單常量和相關行為結果的清單)。 如需依存於地區設定字碼頁而非多位元組字碼頁的多位元組常式清單，請參閱[解譯多位元組字元序列](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。

多位元組字碼頁也會影響下列執行階段程式庫常式的多位元組字元處理︰

||||
|-|-|-|
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

此外,所有接收多位元位元*argv*或*envp*程式參數作為參數(如 **_exec**和 **_spawn**族)的運行時庫例程都根據多位元節代碼頁處理這些字串。 因此,這些例程還受更改多位元組碼頁的 **_setmbcp**調用的影響。

*代碼頁*參數可以設定為以下任意值:

- **_MB_CP_ANSI**在程式啟動時使用從作業系統獲取的 ANSI 代碼頁。

- **_MB_CP_LOCALE**使用從上一個呼叫取得的目前區域設定碼頁[設定區域設定](setlocale-wsetlocale.md)。

- **_MB_CP_OEM**在程式啟動時使用從作業系統獲取的 OEM 代碼頁。

- **_MB_CP_SBCS**使用單位元組碼頁。 當代碼頁設置為 **_MB_CP_SBCS**時[,_ismbblead](ismbblead-ismbblead-l.md)等例程總是返回 false。

- **_MB_CP_UTF8**使用 UTF-8。  當代碼頁設置為 **_MB_CP_UTF8**時[,_ismbblead](ismbblead-ismbblead-l.md)等例程總是返回 false。

- 任何其他有效的代碼頁值,無論該值是 ANSI、OEM 還是其他作業系統支援的代碼頁(不支援的 UTF-7 除外)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
