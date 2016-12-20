---
title: "MFC DLL 可以建立多個執行緒嗎？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 多執行緒"
  - "MFC DLL [C++], 多執行緒"
  - "多執行緒 [C++], DLL"
  - "執行緒 [MFC], DLL"
ms.assetid: 41d5b5e6-a7d3-42bf-b641-f1245abd1c59
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MFC DLL 可以建立多個執行緒嗎？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化期間之外，只要 MFC DLL 使用 Win32 執行緒區域儲存區 \(Thread Local Storage，TLS\) 函式 \(例如 **TlsAlloc**\) 來配置執行緒區域儲存區，它便可以安全地建立多個執行緒。  然而，如果 MFC DLL 使用 **\_\_declspec\(thread\)** 來配置執行緒區域儲存區，用戶端應用程式就必須隱含地連結至 DLL。  如果用戶端應用程式明確地連結至 DLL，**LoadLibrary** 呼叫就無法成功地載入 DLL。  如需在 MFC DLL 內部建立多個執行緒的詳細資訊，請參閱知識庫文件＜PRB: Calling LoadLibrary\(\) to Load a DLL That Has Static TLS＞\(Q118816\)。  
  
 在啟動期間建立新 MFC 執行緒的 MFC DLL 在應用程式載入它時停止回應。  這個部分還包括每當執行緒是在內部呼叫 `AfxBeginThread` 或 `CWinThread::CreateThread` 所建立之時：  
  
-   標準 DLL `CWinApp` 衍生物件的 `InitInstance`  
  
-   標準 DLL 裡提供的 `DllMain` 或 **RawDllMain** 函式  
  
-   擴充 DLL 裡提供的 `DllMain` 或 **RawDllMain** 函式  
  
 如需在初始化過程中建立執行緒的詳細資訊，請參閱知識庫文件＜PRB: Cannot Create an MFC Thread During DLL Startup＞\(Q142243\)。  
  
## 請參閱  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)