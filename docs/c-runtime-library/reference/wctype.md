---
title: wctype
ms.date: 11/04/2016
apiname:
- wctype
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
apitype: DLLExport
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: 81caf8e1ab04635d205d7b01af2d4c2896eec01c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155312"
---
# <a name="wctype"></a>wctype

決定寬字元代碼的分類規則。

## <a name="syntax"></a>語法

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>參數

*屬性*<br/>
屬性字串。

## <a name="return-value"></a>傳回值

如果**LC_CTYPE**目前的地區設定的類別不會定義名稱符合屬性字串的分類規則*屬性*，函數會傳回零。 否則，它會傳回適合用為 [towctrans](towctrans.md) 後續呼叫的第二個引數的非零值。

## <a name="remarks"></a>備註

此函式決定寬字元代碼的分類規則。 下列呼叫組合在所有的地區設定中都有一樣的行為 (但實作即使是在 "C" 地區設定中，也可以定義額外的分類規則)︰

|功能|同於|
|--------------|-------------|
|iswalnum(c)|iswctype(c, wctype( "alnum" ) )|
|iswalpha(c)|iswctype(c, wctype( "alpha" ) )|
|iswcntrl(c)|iswctype(c, wctype( "cntrl" ) )|
|iswdigit(c)|iswctype(c, wctype( "digit" ) )|
|iswgraph(c)|iswctype(c, wctype( "graph" ) )|
|iswlower(c)|iswctype(c, wctype( "lower" ) )|
|iswprint(c)|iswctype(c, wctype( "print" ) )|
|iswpunct(c)|iswctype(c, wctype( "punct" ) )|
|iswspace(c)|iswctype(c, wctype( "space" ) )|
|iswupper(c)|iswctype(c, wctype( "upper" ) )|
|iswxdigit(c)|iswctype(c, wctype( "xdigit" ) )|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
