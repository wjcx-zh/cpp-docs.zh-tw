---
title: fwide | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a055df312215b5ff424aff54cfee54e0568ab307
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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