---
title: wctype | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbad04d3c56015ddea10a058ae8b262d7f94d40f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

如果**LC_CTYPE**目前的地區設定分類的未定義的分類規則，其名稱符合屬性的字串*屬性*，此函數會傳回零。 否則，它會傳回適合用為 [towctrans](towctrans.md) 後續呼叫的第二個引數的非零值。

## <a name="remarks"></a>備註

此函式決定寬字元代碼的分類規則。 下列呼叫組合在所有的地區設定中都有一樣的行為 (但實作即使是在 "C" 地區設定中，也可以定義額外的分類規則)︰

|功能|同於|
|--------------|-------------|
|iswalnum(c)|iswctype (c、 wctype ("與 alnum"))|
|iswalpha(c)|iswctype (c、 wctype ("alpha"))|
|iswcntrl(c)|iswctype (c、 wctype （「 控制項 」）)|
|iswdigit(c)|iswctype (c、 wctype （「 數字 」）)|
|iswgraph(c)|iswctype (c、 wctype （「 圖形 」）)|
|iswlower(c)|iswctype (c、 wctype （「 下方 」）)|
|iswprint(c)|iswctype (c、 wctype ("print"))|
|iswpunct(c)|iswctype (c、 wctype （「 符號 」）)|
|iswspace(c)|iswctype (c、 wctype （「 空間 」）)|
|iswupper(c)|iswctype (c、 wctype （「 上限 」）)|
|iswxdigit(c)|iswctype (c、 wctype (「 xdigit"))|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
