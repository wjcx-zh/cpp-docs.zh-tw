---
title: "Running the Program as a Local Server | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 服務, running as local servers"
  - "偵錯 [ATL], running services as local server"
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Running the Program as a Local Server
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果執行程式做為服務並不方便，可以暫時變更登錄，使程式會以一般本機伺服器。  將 `LocalService` 值就會在您的 AppID 下的 `_LocalService` 並確定您的 CLSID 底下的 `LocalServer32` 索引鍵正確設定。  重新命名 \(使用指定的 DCOMCNFG 有關您的 `LocalServer32` 金鑰組。 `_LocalServer32`\) 的另一部電腦上應該執行應用程式執行程式做為本機伺服器需要一些在開始的詳細的秒數，因為 **StartServiceCtrlDispatcher** 對的呼叫會在 `CAtlServiceModuleT::Start` 需要幾秒鐘的時間，則會失敗。  
  
## 請參閱  
 [Debugging Tips](../atl/debugging-tips.md)