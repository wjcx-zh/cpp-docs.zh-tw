---
title: "Debugging and Error Reporting Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式 [ATL], 錯誤報告"
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debugging and Error Reporting Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式會提供有用的偵錯及追蹤功能。  
  
|||  
|-|-|  
|[AtlHresultFromLastError](../Topic/AtlHresultFromLastError.md)|使用 HRESULT 的形式，傳回 `GetLastError` 錯誤碼。|  
|[AtlHresultFromWin32](../Topic/AtlHresultFromWin32.md)|轉換 Win32 錯誤碼的 HRESULT。|  
|[AtlReportError](../Topic/AtlReportError.md)|設定 **IErrorInfo** 提供錯誤詳細資料寫入至用戶端。|  
|[AtlThrow](../Topic/AtlThrow.md)|擲回 `CAtlException`。|  
|[AtlThrowLastWin32](../Topic/AtlThrowLastWin32.md)|呼叫此函式發出信號根據 Windows 函式 `GetLastError`結果的錯誤。|  
|[AtlTraceLoadSettings](../../misc/atltraceloadsettings.md)|呼叫此函式從檔案載入追蹤設定。|  
|[AtlTraceSaveSettings](../../misc/atltracesavesettings.md)|呼叫此函式將目前追蹤設定至檔案。|  
  
## 請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [Debugging and Error Reporting Macros](../../atl/reference/debugging-and-error-reporting-macros.md)