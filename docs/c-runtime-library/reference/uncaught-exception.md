---
title: __uncaught_exception | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcae75a5d25710866f781d766cfd77eceb977649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="uncaughtexception"></a>__uncaught_exception

表示一或多個例外狀況是否沒有擲回，但尚未處理的對應**攔截**區塊[try catch](../../cpp/try-throw-and-catch-statements-cpp.md)陳述式。

## <a name="syntax"></a>語法

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>傳回值

**true**時擲回例外狀況**再試一次**區塊，直到比對**攔截**區塊是初始化，否則**false**。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>另請參閱

[try、throw 和 catch 陳述式 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
