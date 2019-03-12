---
title: __dllonexit
ms.date: 11/04/2016
apiname:
- __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- __dllonexit
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: a6c077ac010c0b5d94ba21ba823441ea6ac932b9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739371"
---
# <a name="dllonexit"></a>__dllonexit

登錄要在結束時呼叫的常式。

## <a name="syntax"></a>語法

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>參數

*func*<br/>
要在結束時執行的函式指標。

*pbegin*<br/>
變數指標，指向要在中斷連結時執行的函式的清單開頭。

*pend*<br/>
變數指標，指向要在中斷連結時執行的函式的清單結尾。

## <a name="return-value"></a>傳回值

如果成功，則為使用者的函式指標。 否則為 **NULL** 指標。

## <a name="remarks"></a>備註

`__dllonexit` 函式類似 [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) 函式，只不過這個常式看不到該函式所用的全域變數。 此函數使用 `pbegin` 和 `pend` 參數，而不是全域變數。

DLL 中與 MSVCRT.LIB 連結的 `_onexit` 和 `atexit` 函式，必須維護其本身的 atexit/_onexit 清單。 此常式是這類 DLL 呼叫的背景工作。

`_PVFV` 類型定義為 `typedef void (__cdecl *_PVFV)(void)`。

## <a name="requirements"></a>需求

|常式傳回的值|必要檔案|
|-------------|-------------------|
|__dllonexit|onexit.c|

## <a name="see-also"></a>另請參閱

[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
