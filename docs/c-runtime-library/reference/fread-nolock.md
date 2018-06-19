---
title: _fread_nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fread_nolock
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
- _fread_nolock
- fread_nolock
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- fread_nolock function
- _fread_nolock function
- streams [C++], reading data from
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 444a4b371eb6b4add140c5d0d96f48a69e35152c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396705"
---
# <a name="freadnolock"></a>_fread_nolock

從資料流讀取資料，但不鎖定其他執行緒。

## <a name="syntax"></a>語法

```C
size_t _fread_nolock(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
資料的儲存位置。

*size*<br/>
項目大小 (位元組)。

*count*<br/>
要讀取項目的最大數量。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

請參閱 [fread](fread.md)。

## <a name="remarks"></a>備註

此函式為非鎖定版本**fread**。 它相當於**fread**不同之處在於它不受干擾其他執行緒。 因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這個函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fread_nolock**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
