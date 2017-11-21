---
title: _heapchk | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapchk
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
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9fcbafbb98385878dbc84f300e8d2bf0dac581c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="heapchk"></a>_heapchk
在堆積上執行一致性檢查。  
  
## <a name="syntax"></a>語法  
  
```  
int _heapchk( void );  
```  
  
## <a name="return-value"></a>傳回值  
 `_heapchk` 會傳回下列在 Malloc.h 中定義的整數資訊清單常數之一。  
  
 `_HEAPBADBEGIN`  
 初始標頭資訊不正確或找不到。  
  
 `_HEAPBADNODE`  
 找到不正確的節點或堆積損壞。  
  
 `_HEAPBADPTR`  
 無效的堆積指標。  
  
 `_HEAPEMPTY`  
 堆積尚未初始化。  
  
 `_HEAPOK`  
 堆積看似一致。  
  
 此外若是發生錯誤， `_heapchk` 會將 `errno` 設為 `ENOSYS`。  
  
## <a name="remarks"></a>備註  
 `_heapchk` 函式可透過檢查堆積的最小一致性來協助堆積相關問題的偵錯。 若作業系統不支援 `_heapchk` (例如，Windows 98)，此函式會傳回 `_HEAPOK`，並將 `errno` 設為 `ENOSYS`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_heapchk`|\<malloc.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [_heapadd](../../c-runtime-library/heapadd.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)   
 [_heapset](../../c-runtime-library/heapset.md)   
 [_heapwalk](../../c-runtime-library/reference/heapwalk.md)