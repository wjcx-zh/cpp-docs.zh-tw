---
title: __p__fmode
ms.date: 11/04/2016
api_name:
- __p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: 6f7676fc5c9958be3d0567e6bf22a11367094150
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939976"
---
# <a name="__p__fmode"></a>__p__fmode

指向 `_fmode` 全域變數會指定檔案 I/O 作業的預設「檔案轉譯模式」。

## <a name="syntax"></a>語法

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>傳回值

`_fmode` 全域變數的指標。

## <a name="remarks"></a>備註

`__p__fmode` 函式僅供內部使用，不應該從使用者程式碼呼叫。

檔案轉譯模式會指定 [_open](../c-runtime-library/reference/open-wopen.md) 和 [_pipe](../c-runtime-library/reference/pipe.md) I/O 作業的 `binary` 或 `text` 轉譯。 如需詳細資訊，請參閱 [_fmode](../c-runtime-library/fmode.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__p\__fmode|stdlib.h|