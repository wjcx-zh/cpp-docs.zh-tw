---
title: __p__commode
ms.date: 4/2/2020
api_name:
- __p__commode
- _o___p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: fa589c1972d27854e3f794d8283f49d9db5d053a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349312"
---
# <a name="__p__commode"></a>__p__commode

指向 `_commode` 全域變數會指定檔案 I/O 作業的預設「檔案認可模式」**。

## <a name="syntax"></a>語法

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>傳回值

`_commode` 全域變數的指標。

## <a name="remarks"></a>備註

`__p__commode` 函式僅供內部使用，不應該從使用者程式碼呼叫。

檔案認可模式會指定重要資料寫入磁碟的時機。 如需詳細資訊，請參閱 [fflush](../c-runtime-library/reference/fflush.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__p\__commode|internal.h|
