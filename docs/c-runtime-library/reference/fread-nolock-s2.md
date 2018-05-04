---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _fread_nolock_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs:
- C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db0cd82d251595be586b46fb66a0f0262484e2f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="freadnolocks"></a>_fread_nolock_s

從資料流讀取資料，但不鎖定其他執行緒。 這版的 [fread_nolock](fread-nolock.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
資料的儲存位置。

*BufferSize*<br/>
以位元組為單位的目的緩衝區大小。

*elementSize*<br/>
以位元組為單位的讀取項目大小。

*elementCount*<br/>
要讀取項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

請參閱 [fread_s](fread-s.md)。

## <a name="remarks"></a>備註

此函式為非鎖定版本**fread_s**。 它相當於**fread_s**不同之處在於它不受干擾其他執行緒。 因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這個函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fread_nolock_s**|C：\<stdio.h>；C++：\<cstdio> 或 \<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
