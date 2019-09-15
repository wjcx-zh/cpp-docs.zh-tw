---
title: _get_current_locale
ms.date: 11/04/2016
api_name:
- _get_current_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
ms.openlocfilehash: a17e730b350eaf88cf1c51502fda3df5ae30f611
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956084"
---
# <a name="_get_current_locale"></a>_get_current_locale

取得代表目前地區設定的地區設定物件。

## <a name="syntax"></a>語法

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>傳回值

代表目前地區設定的地區設定物件。

## <a name="remarks"></a>備註

**_Get_current_locale**函式會取得執行緒目前設定的地區設定，並傳回代表該地區設定的地區設定物件。

此函式的先前名稱 **__get_current_locale** （含有兩個前置底線）已被取代。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
