---
title: wctype
ms.date: 11/04/2016
api_name:
- wctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: f77082bbcc5f3cd9d82fb40993c3ac678e7e7ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957811"
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

如果目前地區設定的**LC_CTYPE**類別不會定義名稱符合屬性字串*屬性*的分類規則，此函數會傳回零。 否則，它會傳回適合用為 [towctrans](towctrans.md) 後續呼叫的第二個引數的非零值。

## <a name="remarks"></a>備註

此函式決定寬字元代碼的分類規則。 下列呼叫組合在所有的地區設定中都有一樣的行為 (但實作即使是在 "C" 地區設定中，也可以定義額外的分類規則)︰

|函數|同於|
|--------------|-------------|
|iswalnum （c）|iswctype （c，wctype.h> （"alnum"））|
|iswAlpha （c）|iswctype （c，wctype.h> （"Alpha"））|
|iswcntrl(c)|iswctype （c，wctype.h> （"cntrl"））|
|iswdigit(c)|iswctype （c，wctype.h> （"數位"））|
|iswgraph(c)|iswctype （c，wctype.h> （"graph"））|
|iswlower （c）|iswctype （c，wctype.h> （"lower"））|
|iswprint(c)|iswctype （c，wctype.h> （"print"））|
|iswpunct(c)|iswctype （c，wctype.h> （"punct"））|
|iswspace(c)|iswctype （c，wctype.h> （"space"））|
|iswupper （c）|iswctype （c，wctype.h> （"upper"））|
|iswxdigit(c)|iswctype （c，wctype.h> （"xdigit"））|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
