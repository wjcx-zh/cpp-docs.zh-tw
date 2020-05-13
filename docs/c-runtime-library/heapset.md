---
title: _heapset
ms.date: 11/04/2016
api_name:
- _heapset
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapset
- heapset
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
ms.openlocfilehash: 2a0aea37237f04939579eb059a42dd33771339ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351278"
---
# <a name="_heapset"></a>_heapset

檢查堆積是否達到基本的一致性，並將可用的項目設定為指定的值。

> [!IMPORTANT]
> 此函式已過時。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。

## <a name="syntax"></a>語法

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>參數

*填補*<br/>
填滿字元。

## <a name="return-value"></a>傳回值

`_heapset` 會傳回下列在 Malloc.h 中定義的整數資訊清單常數之一。

|||
|-|-|
| `_HEAPBADBEGIN`  | 找不到初始標頭資訊或其無效。  |
| `_HEAPBADNODE`  | 堆積已損毀或找到故障的節點。  |
| `_HEAPEMPTY`  | 堆積未初始化。  |
| `_HEAPOK`  | 堆積看似一致。  |

此外，若是發生錯誤，`_heapset` 會將 `errno` 設為 `ENOSYS`。

## <a name="remarks"></a>備註

`_heapset` 函式會顯示可用的記憶體位置，或不慎被覆寫的節點。

`_heapset` 會檢查堆積是否達到基本的一致性，然後將堆積中可用項目的每個位元組設為 `fill` 值。 這項已知值會顯示堆積中的哪些記憶體位置包含可用的節點，以及所含資料中有哪些不慎被誤寫而釋放出記憶體。 若作業系統不支援 `_heapset` (例如，Windows 98)，此函式會傳回 `_HEAPOK`，並將 `errno` 設為 `ENOSYS`。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|`_heapset`|\<malloc.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱簡介中的 [Compatibility](../c-runtime-library/compatibility.md) 。

## <a name="example"></a>範例

```c
// crt_heapset.c
// This program checks the heap and
// fills in free entries with the character 'Z'.

#include <malloc.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int heapstatus;
   char *buffer;

   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is
      exit( 0 );                        //    initialized
   heapstatus = _heapset( 'Z' );        // Fill in free entries
   switch( heapstatus )
   {
   case _HEAPOK:
      printf( "OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf( "OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
   free( buffer );
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)
