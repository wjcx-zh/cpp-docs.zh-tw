---
title: "CDebugReportHook Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CDebugReportHook"
  - "CDebugReportHook"
  - "ATL::CDebugReportHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDebugReportHook class"
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDebugReportHook Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用這個類別會將偵錯回報給具名管道。  
  
## 語法  
  
```  
  
class CDebugReportHook  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDebugReportHook::CDebugReportHook](../Topic/CDebugReportHook::CDebugReportHook.md)|呼叫 [SetPipeName](../Topic/CDebugReportHook::SetPipeName.md)、 [SetTimeout](../Topic/CDebugReportHook::SetTimeout.md)和 [SetHook](../Topic/CDebugReportHook::SetHook.md)。|  
|[CDebugReportHook::~CDebugReportHook](../Topic/CDebugReportHook::~CDebugReportHook.md)|呼叫 [CDebugReportHook::RemoveHook](../Topic/CDebugReportHook::RemoveHook.md)。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDebugReportHook::CDebugReportHookProc](../Topic/CDebugReportHook::CDebugReportHookProc.md)|\(靜態\) 已連結至 C 執行階段的自訂報告函式偵錯報告程序。|  
|[CDebugReportHook::RemoveHook](../Topic/CDebugReportHook::RemoveHook.md)|呼叫這個方法會停止傳送偵錯回報給具名管道而還原之前報告攔截。|  
|[CDebugReportHook::SetHook](../Topic/CDebugReportHook::SetHook.md)|呼叫這個方法會啟動傳輸偵錯回報至具名管道。|  
|[CDebugReportHook::SetPipeName](../Topic/CDebugReportHook::SetPipeName.md)|呼叫這個方法會設定偵錯報告將傳送管道的電腦和名稱。|  
|[CDebugReportHook::SetTimeout](../Topic/CDebugReportHook::SetTimeout.md)|以毫秒為單位\) 呼叫這個方法會設定時間這個類別會等候具名管道變成可用。|  
  
## 備註  
 建立這個類別的執行個體中偵錯組建服務或應用程式傳送偵錯回報給具名管道。  偵錯回報藉由呼叫 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 或使用包裝函式產生此函式 \(例如 [ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md) 和 [ATLASSERT](../Topic/ATLASSERT.md) 巨集。  
  
 此類別會使用可讓您以互動方式偵錯執行於非互動式 [視窗工作站](http://msdn.microsoft.com/library/windows/desktop/ms687096)的元件。  
  
 請注意使用執行緒本身的安全性內容，，偵錯報告傳送。  模擬暫時停用，讓偵錯報告可以檢視在低權限使用者模擬的情況，例如 Web 應用程式。  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [類別](../../atl/reference/atl-classes.md)