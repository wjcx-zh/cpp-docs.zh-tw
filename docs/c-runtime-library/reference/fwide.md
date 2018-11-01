---
title: fwide
ms.date: 11/04/2016
apiname:
- fwide
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: d992ebc527744beeb4ef14175e3f10646a77a064
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557842"
---
# <a name="fwide"></a>fwide

未實作。

## <a name="syntax"></a>語法

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
指標**檔案**（忽略） 的結構。

*mode*<br/>
資料流的新寬度︰寬字元為正值、位元組為負值、零則保留不變。 (這個值會被忽略。)

## <a name="return-value"></a>傳回值

此函式目前只會傳回*模式*。

## <a name="remarks"></a>備註

此函式的目前版本不符合標準。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

如需詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。