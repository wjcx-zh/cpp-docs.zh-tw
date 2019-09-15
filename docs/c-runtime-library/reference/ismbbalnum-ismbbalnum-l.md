---
title: _ismbbalnum、_ismbbalnum_l
ms.date: 11/04/2016
api_name:
- _ismbbalnum
- _ismbbalnum_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
ms.openlocfilehash: d817ea6875149f9342854b0c22b27b0c93d29636
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954289"
---
# <a name="_ismbbalnum-_ismbbalnum_l"></a>_ismbbalnum、_ismbbalnum_l

判斷指定的多位元組字元為 alpha 或數值。

## <a name="syntax"></a>語法

```C
int _ismbbalnum(
   unsigned int c
);
int _ismbbalnum_l(
   unsigned int c
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果運算式為，則 **_ismbbalnum**會傳回非零值：

`isalnum(c) || _ismbbkalnum(c)`

*c*為非零值; 如果不是，則為0。

具有 **_l**後置字元的這個函式版本是一樣的，不同之處在于它會使用傳入的地區設定，而非目前的地區設定來處理其地區設定相關的行為。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_ismbbalnum**|\<mbctype.h>|
|**_ismbbalnum_l**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
