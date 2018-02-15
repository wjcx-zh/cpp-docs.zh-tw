---
title: set_terminate (CRT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- set_terminate
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
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eba062bd1b791f055b2ae1c74c2a0107a4039d23
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)
安裝您要由 `terminate` 呼叫的專屬終止常式。  
  
## <a name="syntax"></a>語法  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### <a name="parameters"></a>參數  
 `termFunction`  
 所撰寫之終止函式的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回 `set_terminate` 所註冊之先前函式的指標，因此，稍後可以還原先前函式。 如果尚未設定先前函式，傳回值可能用於還原預設行為；這個值可以是 NULL。  
  
## <a name="remarks"></a>備註  
 `set_terminate` 函式透過 `terminate` 呼叫時會安裝 `termFunction`。 `set_terminate` 是與 C++ 例外狀況處理搭配使用，而且可以在擲回例外狀況之前於程式中的任何位置呼叫。 `terminate` 預設會呼叫 `abort`。 您可以變更這個預設值，方法是撰寫您自己的終止函式，並使用您的函式名稱作為引數呼叫 `set_terminate`。 `terminate` 會呼叫指定為 `set_terminate` 之引數的最後一個函式。 執行任何所需的清除工作之後，`termFunction` 應該會結束程式。 如果它未結束 (如果將它傳回至呼叫端)，則會呼叫 `abort`。  
  
 在多執行緒環境中，會分別維護每個執行緒的終止函式。 每個新執行緒都需要安裝它自己的終止函式。 因此，每個執行緒都會負責它自己的終止處理。  
  
 `terminate_function` 類型定義於 EH.H 中，作為傳回 `void` 之使用者定義終止函式 `termFunction` 的指標。 自訂函式 `termFunction` 無法接受任何引數，而且不應該傳回至其呼叫端。 如果是這樣的話，會呼叫 `abort`。 可能不會從 `termFunction` 擲回例外狀況。  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  `set_terminate` 函式僅作用於偵錯工具外部。  
  
 所有動態連結的 DLL 或 EXE 都有一個單一 `set_terminate` 處理常式；即使您呼叫 `set_terminate`，還是會將您的處理常式取代為其他處理常式，或是取代其他 DLL 或 EXE 所設定的處理常式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`set_terminate`|\<eh.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱 [terminate](../../c-runtime-library/reference/terminate-crt.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_get_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)