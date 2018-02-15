---
title: "_cexit、_c_exit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _c_exit
- _cexit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 825ed933d5a164fd6a07f13319d30fdf97a928e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cexit-cexit"></a>_cexit、_c_exit
執行清除作業，並傳回而不終止處理序。  
  
## <a name="syntax"></a>語法  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## <a name="remarks"></a>備註  
 `_cexit` 函式會以後進先出 (LIFO) 的順序呼叫 `atexit` 和 `_onexit` 所註冊的函式。 `_cexit` 接著會清除所有 I/O 緩衝區，並在傳回之前關閉所有開啟的資料流。 `_c_exit` 與 `_exit` 相同，但傳回到呼叫處理序，而不處理 `atexit` 或 `_onexit` 或者清除資料流緩衝區。 下表顯示 `exit`、`_exit`、`_cexit` 和 `_c_exit` 的行為。  
  
|函式|行為|  
|--------------|--------------|  
|`exit`|執行完整的 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|  
|`_exit`|執行快速 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|  
|`_cexit`|執行完整的 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|  
|`_c_exit`|執行快速 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|  
  
 當您呼叫 `_cexit` 或 `_c_exit` 函式時，不會呼叫任何在呼叫時即存在之暫存或自動物件的解構函式。 自動物件定義於未將物件宣告成靜態的函式中。 暫存物件是編譯器所建立的物件。 若要先終結自動物件，再呼叫 `_cexit` 或 `_c_exit`，請明確地呼叫該物件的解構函式，如下所示：  
  
```  
myObject.myClass::~myClass( );  
```  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_cexit`|\<process.h>|  
|`_c_exit`|\<process.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)