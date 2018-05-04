---
title: _heapchk | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _heapchk
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
- _heapchk
- heapchk
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3fc500ee86bde40def0e1e2d3dd3edad3127daf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="heapchk"></a>_heapchk

在堆積上執行一致性檢查。

## <a name="syntax"></a>語法

```C
int _heapchk( void );
```

## <a name="return-value"></a>傳回值

**_heapchk**傳回下列整數資訊清單常數在 Malloc.h 中定義的其中一個。

|傳回值|條件|
|-|-|
**_HEAPBADBEGIN**|初始標頭資訊不正確或找不到。
**_HEAPBADNODE**|找到不正確的節點或堆積損壞。
**_HEAPBADPTR**|無效的堆積指標。
**_HEAPEMPTY**|堆積尚未初始化。
**_HEAPOK**|堆積看似一致。

此外，如果發生錯誤， **_heapchk**設定**errno**至**ENOSYS**。

## <a name="remarks"></a>備註

**_Heapchk**函式可協助偵錯堆積相關的問題的最小堆積的一致性檢查。 如果作業系統不支援 **_heapchk**（例如 Windows 98），則函數會傳回 **_HEAPOK**並設定**errno**至**ENOSYS**.

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
