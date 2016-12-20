---
title: "逐步解說：將 Visual C++ 應用程式部署至應用程式本機資料夾 | Microsoft Docs"
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
  - "部署 Visual C++ 應用程式"
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：將 Visual C++ 應用程式部署至應用程式本機資料夾
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述如何藉由複製檔案部署 Visual C\+\+ 應用程式到它的資料夾。  
  
## 必要條件  
  
-   使用 Visual Studio 的電腦上安裝。  
  
-   沒有 Visual C\+\+ 程式庫的其他電腦。  
  
### 若要將應用程式部署至應用程式本機資料夾  
  
1.  依照中的步驟建立並建置 MFC 應用程式在 [逐步解說：使用安裝專案部署 Visual C\+\+ 應用程式](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
2.  複製適當的 MFC 和 C 執行階段 \(CRT\) 程式庫檔案 \(例如， x86 平台的和 Unicode 支援、複製 mfc100u.dll 和 msvcr100.dll 從\\ Program Files \\ Microsoft Visual Studio 10.0 \\ VC \\ redist \\ x86 \\ —然後貼至\\您的 MFC 專案版本\\資料夾。  如需其他檔案的詳細資訊可能必須複製，請參閱 [決定要轉散發哪些 DLL](../ide/determining-which-dlls-to-redistribute.md)。  
  
3.  在沒有 Visual C\+\+ 程式庫的第二部電腦上執行 MFC 應用程式。  
  
    1.  複製\\ version \\資料夾的內容並貼至位於第二部電腦上的應用程式資料夾。  
  
    2.  在第二部電腦上執行應用程式。  
  
     因為應用程式本機資料夾中有 Visual C\+\+ 程式庫，所以應用程式才能執行成功。  
  
## 請參閱  
 [部署範例](../ide/deployment-examples.md)