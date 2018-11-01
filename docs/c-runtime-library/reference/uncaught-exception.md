---
title: __uncaught_exception
ms.date: 11/04/2016
apiname:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 19d1e18af27722d6f9da39ebaaf6c9415c281849
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579630"
---
# <a name="uncaughtexception"></a>__uncaught_exception

表示一或多個例外狀況是否有已擲回，但尚未處理由相對應**攔截**區塊[try / catch](../../cpp/try-throw-and-catch-statements-cpp.md)陳述式。

## <a name="syntax"></a>語法

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>傳回值

**true**發生例外狀況的時間**試**區塊，直到比對**攔截**區塊已初始化，否則**false**。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>另請參閱

[try、throw 和 catch 陳述式 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
