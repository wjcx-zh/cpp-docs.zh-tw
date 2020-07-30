---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 45f483bcaa397969a81097768ebbd1ed4cda288b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226186"
---
# <a name="_recalloc"></a>_recalloc

**Realloc**和**calloc**的組合。 重新配置記憶體中的陣列，並將其項目初始化為 0。

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

*number*<br/>
項目數。

*size*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**_recalloc**會傳回重新配置 **`void`** （且可能已移動）記憶體區塊的指標。

如果沒有足夠的可用記憶體可將區塊展開為指定的大小，原始區塊會保留不變，而且會傳回**Null** 。

如果要求的大小為零，則會釋放*memblock*所指向的區塊;傳回值為**Null**，而*memblock*是指向釋放的區塊。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要取得以外類型的指標 **`void`** ，請對傳回值使用類型轉換。

## <a name="remarks"></a>備註

**_Recalloc**函式會變更已配置記憶體區塊的大小。 *Memblock*引數會指向記憶體區塊的開頭。 如果*memblock*為**Null**， **_recalloc**的行為會與[calloc](calloc.md)相同，並會配置新的*數位*  *  *大小*位元組區塊。 每個項目都會初始化為 0。 如果*memblock*不是**Null**，它應該是先前對**calloc**、 [malloc](malloc.md)或[realloc](realloc.md)的呼叫所傳回的指標。

因為新的區塊可以在新的記憶體位置中，所以 **_recalloc**傳回的指標不一定是透過*memblock*引數傳遞的指標。

**_recalloc**將**Errno**設定為**ENOMEM** ，如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**recalloc**會呼叫**realloc** ，以便使用 c + + [_set_new_mode](set-new-mode.md)函數來設定新的處理常式模式。 新的處理常式模式指出，在失敗時， **realloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **realloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當 **_recalloc**無法配置記憶體時， **realloc**就會呼叫新的處理常式常式，其方式會與 **`new`** 運算子因相同原因而失敗時所執行的相同。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

或與 NEWMODE.OBJ 連結。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **_recalloc**會解析成[_recalloc_dbg](recalloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**_recalloc**標示為 `__declspec(noalias)` 和 `__declspec(restrict)` ，表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
[受](free.md)<br/>
[連結選項](../../c-runtime-library/link-options.md)<br/>
