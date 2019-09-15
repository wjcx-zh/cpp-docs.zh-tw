---
title: __CxxFrameHandler
ms.date: 11/04/2016
api_name:
- __CxxFrameHandler
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __CxxFrameHandler
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
ms.openlocfilehash: 4cb5ae10d4281c4a7167db7adf4ea6788ad3e3c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944505"
---
# <a name="__cxxframehandler"></a>__CxxFrameHandler

內部 CRT 函式。 供 CRT 用於處理結構化例外狀況框架。

## <a name="syntax"></a>語法

```cpp
EXCEPTION_DISPOSITION __CxxFrameHandler(
      EHExceptionRecord  *pExcept,
      EHRegistrationNode *pRN,
      void               *pContext,
      DispatcherContext  *pDC
   )
```

#### <a name="parameters"></a>參數

*pExcept*<br/>
傳遞至可能的 `catch` 陳述式的例外狀況記錄。

*pRN*<br/>
關於用於處理例外狀況的堆疊框架的動態資訊。 如需詳細資訊，請參閱 ehdata.h。

*pContext*<br/>
內容 (不用於 Intel 處理器)。

*pDC*<br/>
函式進入及堆疊框架的其他資訊。

## <a name="return-value"></a>傳回值

[try-except 陳述式](../cpp/try-except-statement.md)所使用的其中一個「篩選條件運算式」值。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__CxxFrameHandler|excpt.h、ehdata.h|