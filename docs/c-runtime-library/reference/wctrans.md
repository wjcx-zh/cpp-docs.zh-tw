---
title: wctrans | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wctrans
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctrans
dev_langs:
- C++
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dab0f5a55f9ee1df30b0a5f040e7944292b5cf25
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="wctrans"></a>wctrans

決定將一組字元碼對應至另一個。

## <a name="syntax"></a>語法

```C
wctrans_t wctrans(
   const char *property
);
```

### <a name="parameters"></a>參數

*屬性*<br/>
指定其中一個有效轉換的字串。

## <a name="return-value"></a>傳回值

如果**LC_CTYPE**目前的地區設定的類別並未定義的對應，其名稱符合屬性的字串*屬性*，此函數會傳回零。 否則，它會傳回適合用為 [towctrans](towctrans.md) 後續呼叫的第二個引數的非零值。

## <a name="remarks"></a>備註

此函式決定將一組字元碼對應至另一個。

下列呼叫組合在所有的地區設定中都有一樣的行為，但即使是在 "C" 地區設定中，也有可能定義額外的對應︰

|功能|同於|
|--------------|-------------|
|tolower(c)|towctrans (c、 wctrans("towlower"))|
|towupper(c)|towctrans (c、 wctrans("toupper"))|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**wctrans**|\<wctype.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_wctrans.cpp
// compile with: /EHsc
// This example determines a mapping from one set of character
// codes to another.

#include <wchar.h>
#include <wctype.h>
#include <stdio.h>
#include <iostream>

int main()
{
    wint_t c = 'a';
    printf_s("%d\n",c);

    wctrans_t i = wctrans("toupper");
    printf_s("%d\n",i);

    wctrans_t ii = wctrans("towlower");
    printf_s("%d\n",ii);

    wchar_t wc = towctrans(c, i);
    printf_s("%d\n",wc);
}
```

```Output
97
1
0
65
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
