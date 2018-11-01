---
title: isblank、iswblank、_isblank_l、_iswblank_l
ms.date: 11/04/2016
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: eb088c4056e2277e188d7f98a57dd36216d013ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497314"
---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank、iswblank、_isblank_l、_iswblank_l

判斷整數是否代表空白字元。

## <a name="syntax"></a>語法

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

這些常式傳回非零值如果*c*表示特定的空格或水平定位字元或是其中一個地區設定特定的一組字元，用來分隔一行文字中的文字。 **isblank**傳回非零值，如果*c*為空格字元 (0x20) 或水平索引標籤字元 (0x09)。 測試條件的結果**isblank**函式取決於**LC_CTYPE**類別目錄設定的地區設定; 如需詳細資訊，請參閱[setlocale、 _wsetlocale](setlocale-wsetlocale.md). 不需要這些函式的版本 **_l**後置詞使用目前的地區設定，針對任何地區設定相關行為; 沒有版本 **_l**尾碼都相同，不同之處在於它們使用會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**iswblank**傳回非零值，如果*c*是寬字元對應至標準空格或水平定位字元。

行為**isblank**並 **_isblank_l**如果是未定義*c*不是 EOF 或介於 0 到 0xFF 的內含。 使用偵錯 CRT 程式庫時， *c*是不是其中一個值，函式會引發判斷提示。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<ctype.h> 或 \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
