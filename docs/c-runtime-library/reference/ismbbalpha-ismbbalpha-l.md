---
title: _ismbbalpha、_ismbbalpha_l
ms.date: 11/04/2016
api_name:
- _ismbbalpha
- _ismbbalpha_l
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
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
ms.openlocfilehash: fe60eec2eb7f93d866340aabe382bf32d6b04b21
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954250"
---
# <a name="_ismbbalpha-_ismbbalpha_l"></a>_ismbbalpha、_ismbbalpha_l

判斷指定的多位元組字元是否為 alpha。

## <a name="syntax"></a>語法

```C
int _ismbbalpha(
   unsigned int c
);
int _ismbbalpha_l(
   unsigned int c
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果運算式為，則 **_ismbbAlpha**會傳回非零值：

`isalpha(c) || _ismbbkalnum(c)`

*c*為非零值; 如果不是，則為0。 **_ismbbAlpha**會針對任何與地區設定相關的字元設定，使用目前的地區設定。 **_ismbbAlpha_l**是相同的，不同之處在于它會使用傳入的地區設定。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_ismbbalpha**|\<mbctype.h>|
|**_ismbbalpha_l**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
