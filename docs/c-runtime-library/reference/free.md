---
title: free | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- free
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc6dfd832d18dbabc1ebc10aec252cc8afe15346
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402513"
---
# <a name="free"></a>free

取消配置或釋放記憶體區塊。

## <a name="syntax"></a>語法

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*先前配置要釋放的記憶體區塊。

## <a name="remarks"></a>備註

**可用**函式會取消配置的記憶體區塊 (*memblock*) 先前呼叫所配置的**calloc**， **malloc**，或**realloc**。 釋出的位元組數目就相當於要求時已配置區塊的位元組數目 (或重新配置後，如果是**realloc**)。 如果*memblock*是**NULL**，指標就會忽略和**可用**立即傳回。 嘗試釋放指標無效 (未配置的記憶體區塊的指標**calloc**， **malloc**，或**realloc**) 可能會影響後續的配置要求而且會發生錯誤。

如果發生錯誤時即釋放記憶體， **errno**設為從作業系統在本質上失敗的資訊。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

釋放記憶體區塊之後，[_heapmin](heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。

當應用程式的 C 執行階段程式庫的偵錯版本連結時**可用**解析成[_free_dbg](free-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**免費**標示`__declspec(noalias)`，這表示，此函式保證不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

若要釋放使用 [_malloca](malloca.md) 所配置的記憶體，請使用 [_freea](freea.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**free**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [malloc](malloc.md) 的範例。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
