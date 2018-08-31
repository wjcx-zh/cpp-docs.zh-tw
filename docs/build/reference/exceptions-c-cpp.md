---
title: 例外狀況 （C/c + +） |Microsoft Docs
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
ms.openlocfilehash: 40a3a9e1cf1384603d6b7d95fa5960e951f932ef
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216879"
---
# <a name="exceptions-cc"></a>例外狀況 (C/C++)
發生失敗時，可能會引發兩個例外狀況代碼：  
  
-   針對**LoadLibrary**失敗  
  
-   針對**GetProcAddress**失敗  
  
 以下是例外狀況資訊：  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 擲回的例外狀況代碼是標準 VcppException （ERROR_SEVERITY_ERROR、 ERROR_MOD_NOT_FOUND） 和 VcppException （ERROR_SEVERITY_ERROR、 ERROR_PROC_NOT_FOUND） 值。 例外狀況傳遞指標**DelayLoadInfo** LPDWORD 值，可以藉由擷取中的結構**GetExceptionInformation**中[EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record)結構，ExceptionInformation [0] 欄位。  
  
 此外，如果設定不正確的位元 grAttrs 欄位中，ERROR_INVALID_PARAMETER 會擲回例外狀況。 這個例外狀況是，針對所有與目的嚴重威脅。  
  
 請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理和通知](../../build/reference/error-handling-and-notification.md)