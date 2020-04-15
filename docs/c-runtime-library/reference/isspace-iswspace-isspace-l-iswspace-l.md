---
title: isspace、iswspace、_isspace_l、_iswspace_l
ms.date: 4/2/2020
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
- _o_isspace
- _o_iswspace
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: 43d66a191427e886941fd3dcac5dc6b71146b68a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342755"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace、iswspace、_isspace_l、_iswspace_l

判斷整數是否代表空格字元。

## <a name="syntax"></a>語法

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果*c*是空格字元的特定表示形式,則每個例程都返回非零。 如果*c*是空格字元(0x09 - 0x0D 或 0x20),**則 isspace**返回非零值。 **isspace**函數的測試條件的結果取決於區域設置**LC_CTYPE**類別設置;有關詳細資訊[,請參閱集本地設置_wsetlocale。](setlocale-wsetlocale.md) 這些函數的版本沒有 **_l**後綴,因此使用當前區域設置執行任何與區域設置相關的行為;具有 **_l**後綴的版本是相同的,只是它們使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

如果*c*是對應於標準空白字元的寬字元,**則 iswspace**返回非零值。

如果*c*不是 EOF 或範圍 0 到 0xFF(包括)時,**則空間**和 **_isspace_l**的行為未定義。 當使用除錯 CRT 庫,*並且 c*不是這些值之一時,這些函數將引發斷言。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**•** **分空間**|**正空間**|[_ismbcspace](ismbcgraph-functions.md)|**正空間**|

## <a name="remarks"></a>備註

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**正空間**|\<ctype.h>|
|**正空間**|\<ctype.h> 或 \<wchar.h>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字元分類](../../c-runtime-library/character-classification.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[is、isw 常式](../../c-runtime-library/is-isw-routines.md)<br/>
