---
title: free
ms.date: 11/04/2016
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
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: f56212874f05ea5d4ab7bd826a7a4c145551dfc0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621230"
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

*memblock*<br/>
要釋放之先前配置的記憶體區塊。

## <a name="remarks"></a>備註

**免費**函式會取消配置記憶體區塊 (*memblock*) 的先前呼叫所配置**calloc**， **malloc**，或是**realloc**。 釋放的位元組數目相當於配置區塊時所要求的位元組數目 (或重新配置，若是**realloc**)。 如果*memblock*是**NULL**，會忽略指標，並**免費**立即傳回。 嘗試釋放無效指標 (未配置之記憶體區塊指標**calloc**， **malloc**，或**realloc**) 可能會影響後續配置要求導致錯誤。

如果發生錯誤時釋放記憶體**errno**資訊從作業系統在本質上失敗的設定。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

釋放記憶體區塊之後，[_heapmin](heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。

當偵錯版本的 C 執行階段程式庫，連結的應用程式時**免費**解析[_free_dbg](free-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**免費**標示`__declspec(noalias)`，這表示保證函式時，會不能修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

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
