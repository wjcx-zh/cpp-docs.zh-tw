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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: 057a0146aed87a50fc2e8c444b97a8b7b51eada1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919505"
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

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__p\__commode|internal.h|
