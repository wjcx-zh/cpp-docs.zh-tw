---
title: _free_locale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b74725ddd7884bcc714e1048b28c53f201ebe4e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="freelocale"></a>_free_locale

釋放地區設定物件。

## <a name="syntax"></a>語法

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*地區設定*釋放的地區設定物件。

## <a name="remarks"></a>備註

**_Free_locale**函數用來釋放取自呼叫的地區設定物件 **_get_current_locale**或 **_create_locale**。

舊名稱的這個函式， **__free_locale** （具有兩個前置底線） 已被取代。

## <a name="requirements"></a>需求

|**常式**|必要的標頭|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
