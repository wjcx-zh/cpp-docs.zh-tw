---
title: _flushall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _flushall
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
- _flushall
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25e8a0045758d22a9b519cd1ffe4cc675a7674c2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="flushall"></a>_flushall
清除所有資料流；清除所有緩衝區。  
  
## <a name="syntax"></a>語法  
  
```  
int _flushall( void );  
```  
  
## <a name="return-value"></a>傳回值  
 `_flushall` 會傳回開啟的資料流數目 (輸入和輸出)。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 根據預設，`_flushall` 函式會將與開啟輸出資料流相關聯之所有緩衝區的內容寫入至適當的檔案。 會清除與開啟之輸入資料流相關聯的所有緩衝區中的目前內容 (這些緩衝區通常是由作業系統所維護，以判斷將資料自動寫入至磁碟的最佳時機︰緩衝區已滿時、關閉資料流時，或程式正常結束而未關閉資料流時)。  
  
 如果在呼叫 `_flushall` 之後讀取，則會將新資料從輸入檔讀入緩衝區。 呼叫 `_flushall` 之後，所有資料流都會保持開啟狀態。  
  
 執行階段程式庫的認可到磁碟功能可讓您確保將重大資料直接寫入至磁碟，而不是作業系統緩衝區。 不需要重新撰寫現有程式，即可連結程式的物件檔案與 Commode.obj 來啟用這項功能。在產生的可執行檔中，`_flushall` 呼叫會將所有緩衝區的內容寫入至磁碟。 Commode.obj 只會影響 `_flushall` 和 `fflush`。  
  
 如需控制認可到磁碟功能的資訊，請參閱[資料流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](../../c-runtime-library/reference/fopen-wfopen.md) 和 [_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_flushall`|\<stdio.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
```Output  
There were 3 streams flushed  
```  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_commit](../../c-runtime-library/reference/commit.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)