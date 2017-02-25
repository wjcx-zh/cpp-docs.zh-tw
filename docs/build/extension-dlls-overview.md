---
title: "擴充 DLL：概觀 | Microsoft Docs"
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
  - "AFXDLL 程式庫"
  - "DLL [C++], 擴充功能"
  - "擴充 DLL [C++], 關於擴充 DLL"
  - "MFC DLL [C++], 擴充 DLL"
  - "共用的 DLL 版本 [C++]"
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 擴充 DLL：概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 擴充 DLL 通常是實作現有 MFC 程式庫類別所衍生的重複使用類別之 DLL。  擴充 DLL 是使用 MFC 的動態連結程式庫版本 \(也稱為 MFC 的共用版本\) 所建置的。  只有以 MFC 的共用版本所建置的 MFC 可執行檔 \(應用程式或標準 DLL\) 可以使用擴充 DLL。  使用擴充 DLL，您可以從 MFC 衍生新的自訂類別，然後將這個 MFC 的擴充版本提供給呼叫您 DLL 的應用程式。  
  
 擴充 DLL 也可以用來在應用程式和 DLL 之間傳遞 MFC 衍生物件。  與傳遞物件關聯的成員函式存在於建立物件的模組裡。  因為使用共用的 MFC DLL 版本時會適當地匯出這些函式，所以您可以在應用程式和它所載入的擴充 DLL 之間自由地傳遞 MFC 或 MFC 衍生物件指標。  
  
 如需滿足擴充 DLL 基本要求的 DLL 範例，請參閱 MFC [DLLHUSK](http://msdn.microsoft.com/zh-tw/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 範例。  請特別注意 Testdll1.cpp 和 Testdll2.cpp 檔案。  
  
 請注意，Visual C\+\+ 文件不再使用 AFXDLL 詞彙。  擴充 DLL 和之前的 AFXDLL 有相同的特性。  
  
## 您想要執行甚麼工作？  
  
-   [初始化擴充 DLL](../build/initializing-extension-dlls.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [擴充 DLL](../build/extension-dlls.md)  
  
-   [在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [建立 MFC DLL](../mfc/reference/mfc-dll-wizard.md)  
  
## 請參閱  
 [DLL 的類型](../build/kinds-of-dlls.md)