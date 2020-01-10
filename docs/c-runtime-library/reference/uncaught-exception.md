---
title: __uncaught_exception
ms.date: 11/04/2016
api_name:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 0130776ec2511aefd42d1700f950d97738e9fb14
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945954"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

指出是否已擲回一或多個例外狀況，但尚未由[try catch](../../cpp/try-throw-and-catch-statements-cpp.md)語句的對應**catch**區塊處理。

## <a name="syntax"></a>語法

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>傳回值

**從在 try 區塊中擲**回例外狀況的時間開始，直到符合的**catch**區塊初始化為止。否則**為 false**。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>另請參閱

[try、throw 和 catch 陳述式 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
