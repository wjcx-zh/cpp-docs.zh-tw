---
title: _set_error_mode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_error_mode
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
- set_error_mode
- _set_error_mode
dev_langs:
- C++
helpviewer_keywords:
- _set_error_mode function
- set_error_mode function
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bae0e413e46776d9d0df0508a30905b9fdb09062
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="seterrormode"></a>_set_error_mode
修改 `__error_mode` 來判斷非預設位置，其中 C 執行階段寫入可能結束程式之錯誤的錯誤訊息。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>語法  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### <a name="parameters"></a>參數  
 `modeval`  
 錯誤訊息的目的地。  
  
## <a name="return-value"></a>傳回值  
 如果發生錯誤，則會傳回舊設定或 -1。  
  
## <a name="remarks"></a>備註  
 設定 `__error_mode` 的值，以控制錯誤輸出接收。 例如，您可以將輸出導向至標準錯誤，或使用 `MessageBox` API。  
  
 可以將 `modeval` 參數設為下列其中一個值。  
  
|參數|描述|  
|---------------|-----------------|  
|`_OUT_TO_DEFAULT`|錯誤接收是透過 `__app_type` 所決定。|  
|`_OUT_TO_STDERR`|錯誤接收是標準錯誤。|  
|`_OUT_TO_MSGBOX`|錯誤接收是訊息方塊。|  
|`_REPORT_ERRMODE`|報告目前 `__error_mode` 值。|  
  
 如果傳入非列出的值，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`_set_error_mode` 會將 `errno` 設為 `EINVAL`，並傳回 -1。  
  
 將它與[判斷提示](../../c-runtime-library/reference/assert-macro-assert-wassert.md)搭配使用時，`_set_error_mode` 會在對話方塊中顯示失敗的陳述式，並提供選項讓您選擇 `Ignore` 按鈕，以繼續執行程式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_set_error_mode`|\<stdlib.h>|  
  
## <a name="example"></a>範例  
  
```C  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
```Output  
Assertion failed: 2+2==5, file crt_set_error_mode.c, line 8  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>請參閱  
 [assert 巨集、_assert、_wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)