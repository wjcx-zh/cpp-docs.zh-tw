---
title: _free_locale
ms.date: 11/04/2016
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
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 92dc8cd711087e8e797b484d6c7e3c6c3b031b5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333036"
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

*locale*<br/>
要釋放的地區設定物件。

## <a name="remarks"></a>備註

**_Free_locale**函數用來釋放呼叫所取得的地區設定物件 **_get_current_locale**或是 **_create_locale**。

先前的名稱，此函式 **__free_locale** （含兩個前置底線） 已被取代。

## <a name="requirements"></a>需求

|**Routine**|必要的標頭|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
