---
title: _ismbbalpha、_ismbbalpha_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ismbbalpha
- _ismbbalpha_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
dev_langs:
- C++
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3e1a5984333def50c31ed6395265afb424fd7e6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="ismbbalpha-ismbbalphal"></a>_ismbbalpha、_ismbbalpha_l

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

**_ismbbalpha**傳回非零值，如果運算式：

`isalpha(c) || _ismbbkalnum(c)`

非零代表*c*，或如果不是 0。 **_ismbbalpha**針對任何地區設定相關的字元設定使用目前的地區設定。 **_ismbbalpha_l**是完全相同，不同之處在於它會使用傳入的地區設定。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_ismbbalpha**|\<mbctype.h>|
|**_ismbbalpha_l**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
