---
title: fwide | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd52c450e2eb34c40d44d00a76550c401abcb6c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
指標**檔案**結構 （忽略）。

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