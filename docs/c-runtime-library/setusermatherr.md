---
title: __setusermatherr
ms.date: 11/04/2016
apiname:
- __setusermatherr
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __setusermatherr
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
ms.openlocfilehash: 116abd203cc289c63535a8e41a005a6fd248b08b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640462"
---
# <a name="setusermatherr"></a>__setusermatherr

指定用使用者提供的常式處理算術錯誤，不用 [_matherr](../c-runtime-library/reference/matherr.md) 常式。

## <a name="syntax"></a>語法

```cpp
void __setusermatherr(
   _HANDLE_MATH_ERROR pf
   )
```

#### <a name="parameters"></a>參數

*pf*<br/>
使用者提供的 `_matherr` 實作指標。

*pf* 參數的類型會宣告為 `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`。

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|__setusermatherr|matherr.c|