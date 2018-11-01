---
title: _recalloc
ms.date: 11/04/2016
apiname:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 3bcc238dcb950a8e30af16efc557e99d933efe92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436513"
---
# <a name="recalloc"></a>_recalloc

組合**realloc**並**calloc**。 重新配置記憶體中的陣列，並將其項目初始化為 0。

## <a name="syntax"></a>語法

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
先前配置之記憶體區塊的指標。

*數字*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**_recalloc**會傳回**void**重新配置後 （且可能有移動） 記憶體區塊的指標。

如果沒有足夠的可用記憶體將區塊展開為指定大小，原始區塊會保持不變，並**NULL**會傳回。

如果要求的大小為零，則所指向的區塊*memblock*釋放; 傳回值是**NULL**，並*memblock*保持指向已釋放的區塊。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得的指標類型以外的其他**void**，使用類型轉換的傳回值。

## <a name="remarks"></a>備註

**_Recalloc**函式會變更已配置的記憶體區塊的大小。 *Memblock*引數指向記憶體區塊的開頭。 如果*memblock*是**NULL**， **_recalloc**行為方式與[calloc](calloc.md)並配置的新區塊*數目* * *大小*位元組。 每個元素都會初始化為 0。 如果*memblock*不是**NULL**，它應該是由先前呼叫所傳回的指標**calloc**， [malloc](malloc.md)，或[realloc](realloc.md).

因為新區塊可能會在新的記憶體位置，傳回的指標 **_recalloc**不保證是透過傳遞指標*memblock*引數。

**_recalloc**設定**errno**要**ENOMEM**如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**呼叫**realloc**若要使用 c + + [_set_new_mode](set-new-mode.md)函式來設定新的處理常式模式。 新的處理常式模式會指出是否在失敗時， **realloc**就是呼叫所設定的新處理常式[_set_new_handler](set-new-handler.md)。 根據預設， **realloc**不會呼叫新的處理常式無法配置記憶體。 您可以覆寫此預設行為，讓，當 **_recalloc**無法配置記憶體， **realloc**呼叫新的處理常式在相同方式來**新**運算子執行時相同的原因而失敗。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

或與 NEWMODE.OBJ 連結。

當偵錯版本的 C 執行階段程式庫，連結的應用程式時 **_recalloc**解析[_recalloc_dbg](recalloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**標示`__declspec(noalias)`和`__declspec(restrict)`，這表示保證函式不能修改全域變數，並傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[連結選項](../../c-runtime-library/link-options.md)<br/>
