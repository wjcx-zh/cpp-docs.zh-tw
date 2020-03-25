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
ms.openlocfilehash: 2364a22d52c5bc418e4499a4a639c8e06559063a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171446"
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

檔案轉譯模式會指定 `binary`_open`text` 和 [_pipe](../c-runtime-library/reference/open-wopen.md) I/O 作業的 [ 或 ](../c-runtime-library/reference/pipe.md) 轉譯。 如需詳細資訊，請參閱 [_fmode](../c-runtime-library/fmode.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
