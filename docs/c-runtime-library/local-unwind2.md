---
title: _local_unwind2
ms.date: 11/04/2016
apiname:
- _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: 8ae5c3937c9dedc54f0a936b91963419d59f79cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535404"
---
# <a name="localunwind2"></a>_local_unwind2

內部 CRT 函式。 執行指定範圍資料表中列出的終止處理常式。

## <a name="syntax"></a>語法

```
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

## <a name="see-also"></a>請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)