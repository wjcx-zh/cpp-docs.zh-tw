---
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 8d9458529e5772f31e3ae5463d3a6ff5a7b726e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940452"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

將一個字元字串對應至另一個字元字串，並執行指定的地區設定相關轉換。 此函式也可用來產生輸入字串的排序鍵。

## <a name="syntax"></a>語法

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>參數

*地區設定*<br/>
地區設定識別項。 地區設定會提供用於字串對應或排序鍵產生的內容。 應用程式可以使用 `MAKELCID` 巨集來建立地區設定識別項。

*dwMapFlags*<br/>
字串對應或排序鍵產生期間所要使用的轉換類型。

*lpSrcStr*<br/>
函式對應或用於排序鍵產生的來源字串指標。 此參數會假設為 Unicode 字串。

*cchSrc*<br/>
`lpSrcStr` 參數所指向之字串的大小 (以字元為單位)。 此計數可選擇性地包含 Null 結束字元。

`cchSrc` 值 -1 指定 `lpSrcStr` 所指向的字串是以 null 終止的。 如果是這種情況，而且此函式是在其字串對應模式下使用，則該函式會計算字串本身長度，並以 null 終止儲存在 `*lpDestStr`中的對應字串。

*lpDestStr*<br/>
函式用來儲存對應字串或排序鍵之緩衝區的長指標。

*cchDest*<br/>
`lpDestStr`所指向之緩衝區的大小 (以字元為單位)。

## <a name="return-value"></a>傳回值

如果 `cchDest` 的值非零，寫入緩衝區的字元數或位元組 (指定 `LCMAP_SORTKEY` 時) 會表示成功。 此計數包含留給 Null 結束字元的空間。

如果 `cchDest` 的值為零，接收翻譯字串或排序鍵所需的緩衝區大小 (以字元為單位) 或位元組 (指定 `LCMAP_SORTKEY` 時) 會表示成功。 此大小包含留給 Null 結束字元的空間。

零表示失敗。 若要取得延伸錯誤資訊，請呼叫 `GetLastError` 函式。

## <a name="remarks"></a>備註

如果 `cchSrc` 大於零且 `lpSrcStr` 為以 null 終止的字串， `__crtLCMapStringW` 會將 `cchSrc` 設定為字串的長度。 然後 `__crtLCMapStringW` 會呼叫寬字串 (Unicode) 版本的 `LCMapString` 函式並指定其參數。 如需此函式的參數和傳回值詳細資訊，請參閱 [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|