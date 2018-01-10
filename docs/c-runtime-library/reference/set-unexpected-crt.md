---
title: set_unexpected (CRT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: set_unexpected
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
apitype: DLLExport
f1_keywords: set_unexpected
dev_langs: C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2798fff46d40ed6100f101cbc8839ad2fd166f4b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)
安裝您要由 `unexpected` 呼叫的專屬終止函式。  
  
## <a name="syntax"></a>語法  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### <a name="parameters"></a>參數  
 `unexpFunction`  
 撰寫以取代 `unexpected` 函式的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回 `_set_unexpected` 所註冊之先前終止函式的指標，因此，稍後可以還原先前函式。 如果尚未設定先前函式，傳回值可能用於還原預設行為；這個值可以是 NULL。  
  
## <a name="remarks"></a>備註  
 `set_unexpected` 函式透過 `unexpected` 呼叫時會安裝 `unexpFunction`。 `unexpected` 未用於目前 C++ 例外狀況處理實作中。 `unexpected_function` 類型定義於 EH.H 中，作為傳回 `void` 之使用者定義非預期函式 `unexpFunction` 的指標。 自訂 `unexpFunction` 函式不應該傳回至其呼叫端。  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 根據預設，`unexpected` 會呼叫 `terminate`。 您可以變更這個預設行為，方法是撰寫您自己的終止函式，並使用您的函式名稱作為引數呼叫 `set_unexpected`。 `unexpected` 會呼叫指定為 `set_unexpected` 之引數的最後一個函式。  
  
 與 `set_terminate` 呼叫所安裝的自訂終止函式不同，可以從 `unexpFunction` 擲回例外狀況。  
  
 在多執行緒環境中，會分別維護每個執行緒的未預期函式。 每個新執行緒都需要安裝它自己的未預期函式。 因此，每個執行緒都會負責它自己的未預期處理。  
  
 在目前的 Microsoft C++ 例外狀況處理實作中，`unexpected` 預設會呼叫 `terminate`，而且例外狀況處理執行階段程式庫絕不會呼叫它。 呼叫 `unexpected` 而非 `terminate` 並沒有任何特定優點。  
  
 所有動態連結的 DLL 或 EXE 都有一個單一 `set_unexpected` 處理常式；即使您呼叫 `set_unexpected`，還是會將您的處理常式取代為其他處理常式，或是取代其他 DLL 或 EXE 所設定的處理常式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`set_unexpected`|\<eh.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [_get_unexpected](../../c-runtime-library/reference/get-unexpected.md)   
 [set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)