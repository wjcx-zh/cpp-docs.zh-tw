---
title: _set_new_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_new_mode
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
- set_new_mode
- _set_new_mode
dev_langs: C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 31a738319507f13dc26346b237447b37ee60ce0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="setnewmode"></a>_set_new_mode
為 `malloc` 設定新的處理常式模式。  
  
## <a name="syntax"></a>語法  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `newhandlermode`  
 `malloc` 的新處理常式模式；有效值為 0 或 1。  
  
## <a name="return-value"></a>傳回值  
 傳回為 `malloc` 設定的前一個處理常式模式。 傳回值 1 表示無法配置記憶體時，`malloc` 之前會呼叫新的處理常式模式；傳回值 0 則表示不會呼叫。 如果`newhandlermode`引數不等於 0 或 1，傳回-1。  
  
## <a name="remarks"></a>備註  
 C++ `_set_new_mode` 函式會設定 [malloc](../../c-runtime-library/reference/malloc.md) 的新處理常式模式。 新的處理常式模式表示失敗時，`malloc` 是否呼叫 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 所設定的新處理常式。 根據預設，`malloc` 不會在失敗時呼叫新的處理常式來配置記憶體。 您可以覆寫這個預設行為，因此，在 `malloc` 無法配置記憶體時，`malloc` 會呼叫新的處理常式，其方法與 `new` 運算子因相同原因而失敗時所執行的方法相同。 如需詳細資訊，請參閱《C++ 語言參考》中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 運算子。 若要覆寫預設值，請及早在程式中呼叫：  
  
```  
_set_new_mode(1)  
```  
  
 ，或使用 Newmode.obj 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。  
  
 這個函式會驗證其參數。 如果 `newhandlermode` 是 0 或 1 以外的值，則此函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，則 **_**`set_new_mode` 會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_set_new_mode`|\<new.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)   
 [_query_new_mode](../../c-runtime-library/reference/query-new-mode.md)