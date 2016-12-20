---
title: "例外狀況 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ERROR_MOD_NOT_FOUND"
  - "vcppException"
  - "ERROR_SEVERITY_ERROR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, DLL 的延遲載入"
  - "DLL 的延遲載入, 例外狀況"
  - "ERROR_MOD_NOT_FOUND 例外狀況"
  - "ERROR_SEVERITY_ERROR 例外狀況"
  - "vcppException"
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 例外狀況 (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果遇到錯誤，會引發兩個例外狀況代碼：  
  
-   **LoadLibrary** 錯誤的代碼  
  
-   **GetProcAddress** 錯誤的代碼  
  
 以下是例外狀況資訊：  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 擲回的例外狀況代碼是標準的 VcppException\(ERROR\_SEVERITY\_ERROR, ERROR\_MOD\_NOT\_FOUND\) 和 VcppException\(ERROR\_SEVERITY\_ERROR, ERROR\_PROC\_NOT\_FOUND\) 值。  例外狀況會在 [EXCEPTION\_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) 結構的 ExceptionInformation\[0\] 欄位中傳遞 LPDWORD 值 \(指向 **DelayLoadInfo** 結構的指標\)，該值可以透過 **GetExceptionInformation** 來擷取。  
  
 此外，如果 grAttrs 欄位中的位元設定錯誤時，將擲回例外狀況 ERROR\_INVALID\_PARAMETER。  不論任何意圖和目的，這個例外狀況都是嚴重的。  
  
 如需詳細資訊，請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)。  
  
## 請參閱  
 [錯誤處理和告知](../../build/reference/error-handling-and-notification.md)