---
title: _getmbcp
ms.date: 11/04/2016
api_name:
- _getmbcp
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
- _getmbcp
- getmbcp
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
ms.openlocfilehash: 0fb7ee6686de5d1c9d1df0efa7fb6b619aef0d7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955020"
---
# <a name="_getmbcp"></a>_getmbcp

擷取目前的字碼頁。

## <a name="syntax"></a>語法

```C
int _getmbcp( void );
```

## <a name="return-value"></a>傳回值

傳回目前的多位元組字碼頁。 傳回值 0 表示使用中的是單一位元組字碼頁。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getmbcp**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_setmbcp](setmbcp.md)<br/>
