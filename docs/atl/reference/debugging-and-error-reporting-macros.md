---
title: "Debugging and Error Reporting Macros | Microsoft Docs"
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
  - "巨集, 錯誤報告"
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debugging and Error Reporting Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些巨集提供有用的偵錯及追蹤功能。  
  
|||  
|-|-|  
|[\_ATL\_DEBUG\_INTERFACES](../Topic/_ATL_DEBUG_INTERFACES.md)|寫入，至輸出視窗，偵測到的任何介面遺漏，當 `_Module.Term` 呼叫。|  
|[\_ATL\_DEBUG\_QI](../Topic/_ATL_DEBUG_QI.md)|將 `QueryInterface` 撰寫所有呼叫至輸出視窗。|  
|[ATLASSERT](../Topic/ATLASSERT.md)|執行與相同的 [\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集在 C 執行階段程式庫中找到的功能。|  
|[ATLENSURE](../Topic/ATLENSURE.md)|會執行參數驗證。  視需要呼叫 `AtlThrow`|  
|[ATLTRACENOTIMPL](../Topic/ATLTRACENOTIMPL.md)|將訊息傳送至傾印裝置所指定的未實作函式。|  
|[ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md)|警告移到另一組輸出裝置報告，例如偵錯工具視窗，根據所指示的旗標和層級。  為了回溯相容性 \(Backward Compatibility\)。|  
|[ATLTRA CE2](../Topic/ATLTRACE2.md)|警告移到另一組輸出裝置報告，例如偵錯工具視窗，根據所指示的旗標和層級。|  
  
## 請參閱  
 [Macros](../../atl/reference/atl-macros.md)   
 [Debugging and Error Reporting Global Functions](../../atl/reference/debugging-and-error-reporting-global-functions.md)