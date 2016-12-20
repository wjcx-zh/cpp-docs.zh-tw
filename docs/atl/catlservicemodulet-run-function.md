---
title: "CAtlServiceModuleT::Run Function | Microsoft Docs"
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
  - "CServiceModule::Run"
  - "CServiceModule.Run"
  - "CSecurityDescriptor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 服務, 安全性"
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlServiceModuleT::Run Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**執行** 包含呼叫 `PreMessageLoop`、 `RunMessageLoop`和 `PostMessageLoop`。  在呼叫後， `PreMessageLoop` 先儲存服務的執行緒 ID.  使用 Win32 API 函式， [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946)，服務會使用這個 ID 是藉由傳送訊息 **WM\_QUIT** 自行關閉。  
  
 `PreMessageLoop` 然後呼叫 `InitializeSecurity`。  根據預設， `InitializeSecurity` 呼叫具有設定的安全性描述元的 [CoInitializeSecurity](http://msdn.microsoft.com/library/windows/desktop/ms693736) NULL，也就是說，所有使用者都可以存取您的物件。  
  
 如果您不想服務指定它的安全性，覆寫 `PreMessageLoop` ，並且不呼叫 `InitializeSecurity`，然後， COM 會判斷安全性設定從登錄。  有一種簡便的方法設定登錄設定與本節稍後討論的 [DCOMCNFG](../atl/dcomcnfg.md) 公用程式。  
  
 一旦安全性物件，指定要向 COM 註冊，將新的用戶端才能連接至。  最後，程式呼叫服務控制管理員 \(SCM\) 執行程式，並輸入訊息迴圈。  程式保持執行，直到公告一個中止的訊息在服務關閉。  
  
## 請參閱  
 [服務](../atl/atl-services.md)   
 [CSecurityDesc Class](../atl/reference/csecuritydesc-class.md)   
 [CSid Class](../atl/reference/csid-class.md)   
 [CDacl Class](../atl/reference/cdacl-class.md)   
 [CAtlServiceModuleT::Run](../Topic/CAtlServiceModuleT::Run.md)