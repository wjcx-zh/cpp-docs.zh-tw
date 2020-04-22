---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: cbcc0c6177ba4cc449daf6a385a7cce53b8c1230
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745336"
---
# <a name="_local_unwind2"></a>_local_unwind2

內部 CRT 函式。 執行指定範圍資料表中列出的終止處理常式。

## <a name="syntax"></a>語法

```cpp
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>參數

*xr*<br/>
[in] 與某個範圍資料表相關的註冊記錄。

*stop*<br/>
[in] 指出 `_local_unwind2` 應停止的語彙層級。

## <a name="remarks"></a>備註

此方法僅用於執行階段環境。 請勿在您的程式碼中呼叫此方法。

當此方法執行終止處理常式時，會從目前的語彙層級開始進行，直到達到 `stop` 指定的層級為止。 此方法不會執行 `stop` 所指定之層級上的終止處理常式。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
