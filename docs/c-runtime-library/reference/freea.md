---
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: dcad8bea4f8cec28d8cb15a9937b1032593ef0cc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956715"
---
# <a name="_freea"></a>_freea

取消配置或釋放記憶體區塊。

## <a name="syntax"></a>語法

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
要釋放之先前配置的記憶體區塊。

## <a name="return-value"></a>傳回值

無。

## <a name="remarks"></a>備註

**_Freea**函式會將先前呼叫所配置的記憶體區塊（*memblock*）解除配置給[_malloca](malloca.md)。 **_freea**會檢查是否已在堆積或堆疊上配置記憶體。 如果它是在堆疊上配置， **_freea**就不會執行任何作業。 如果配置於堆積，所釋放的位元組數目相當於配置區塊時所要求的位元組數目。 如果*memblock*為**Null**，則會忽略指標，而 **_freea**會立即傳回。 嘗試釋放無效指標（不是由 **_malloca**所配置的記憶體區塊指標）可能會影響後續配置要求，並導致錯誤。

如果 **_freea**發現記憶體是配置在堆積上，則會在內部**免費**呼叫。 記憶體在堆積還是堆疊上取決於在記憶體之已配置記憶體正前方的位址所放置的標記。

如果釋放記憶體時發生錯誤，則會在失敗的本質中，使用作業系統的資訊來設定**errno** 。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

釋放記憶體區塊之後，[_heapmin](heapmin.md) 會聯合未使用的區域並將它們釋放回作業系統，以將堆積上的可用記憶體數量降到最低。 未釋放給作業系統的已釋放記憶體會還原到可用集區，並且再度可供重新配置。

呼叫 **_freea**必須伴隨所有對 **_malloca**的呼叫。 同時在相同的記憶體上呼叫 **_freea**兩次也是錯誤。 當應用程式連結到 C 執行時間程式庫的 debug 版本時，特別是藉由定義 **_CRTDBG_MAP_ALLOC**而啟用[_malloc_dbg](malloc-dbg.md)功能時，更容易找到 **_freea**的遺失或重複呼叫。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_freea**標示`__declspec(noalias)`為，表示保證函式不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_freea**|\<stdlib.h> 和 \<malloc.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_malloca](malloca.md) 的範例。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
