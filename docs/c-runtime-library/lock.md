---
title: _lock
ms.date: 11/04/2016
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: c2e57af90bb9b7c6a4ba0e9efdd1dc1dc0bdb985
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606891"
---
# <a name="lock"></a>_lock

取得多執行緒的鎖定。

> [!IMPORTANT]
>  此函式已過時。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。

## <a name="syntax"></a>語法

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>參數

*locknum*<br/>
[in] 要取得之鎖定的識別碼。

## <a name="remarks"></a>備註

若已取得鎖定，此方法仍會取得鎖定，並因而導致內部的 C 執行階段 (CRT) 錯誤。 若方法無法取得鎖定，會結束並引發嚴重錯誤，同時將錯誤碼設為 `_RT_LOCK`。

## <a name="requirements"></a>需求

**來源：** mlock.c

## <a name="see-also"></a>請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)