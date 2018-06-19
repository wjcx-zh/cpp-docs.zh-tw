---
title: 例外狀況 （C/c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
dev_langs:
- C++
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 819f9424b2439cc49517afe54d62a8ed4f06d22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373383"
---
# <a name="exceptions-cc"></a>例外狀況 (C/C++)
發生失敗時，可能會引發兩個例外狀況代碼：  
  
-   如**LoadLibrary**失敗  
  
-   如**GetProcAddress**失敗  
  
 以下是例外狀況資訊：  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 擲回的例外狀況代碼是標準 VcppException （ERROR_SEVERITY_ERROR、 ERROR_MOD_NOT_FOUND） 和 VcppException （ERROR_SEVERITY_ERROR、 ERROR_PROC_NOT_FOUND） 值。 例外狀況會傳遞指標**DelayLoadInfo**結構，可以藉由擷取 LPDWORD 值中的**GetExceptionInformation**中[EXCEPTIONRECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082)結構，ExceptionInformation [0] 欄位。  
  
 此外，如果 grAttrs 欄位設定不正確的位元，ERROR_INVALID_PARAMETER 擲回例外狀況。 這個例外狀況是，不管您的目的，嚴重。  
  
 請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理和通知](../../build/reference/error-handling-and-notification.md)