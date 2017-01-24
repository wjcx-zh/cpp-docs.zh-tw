---
title: "建立僅含資源的 DLL | Microsoft Docs"
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
  - "DLL [C++], 建立"
  - "僅含資源的 DLL [C++], 建立"
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建立僅含資源的 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

僅含資源的 DLL 是指僅包含資源而不包含其他項目的 DLL，例如，圖示、點陣圖、字串和對話方塊。  使用僅含資源的 DLL 是在多個程式間共用一組相同資源的好方法，  也是為應用程式提供當地語系化為多國語言的資源的好方法 \(請參閱 [MFC 應用程式中的當地語系化資源：附屬 DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)\)。  
  
 若要建立僅含資源的 DLL，請建立新 Win32 DLL \(非 MFC\) 專案，並且將您的資源加入專案。  
  
-   在 \[**新增專案**\] 對話方塊中選取 \[Win32 專案\]，並且在 \[Win32 專案精靈\] 中指定 DLL 專案類型。  
  
-   為 DLL 建立包含資源 \(例如字串或功能表\) 的新資源指令碼，並儲存該 .rc 檔案。  
  
-   在 \[專案\] 功能表上，按一下 \[**加入現有項目**\]，並且將新的 .rc 檔案插入至專案。  
  
-   指定 [\/NOENTRY](../build/reference/noentry-no-entry-point.md) 連結器選項。\/NOENTRY 可以防止連結器將 \_main 參考連結至 DLL；建立僅含資源的 DLL 時需要這個選項。  
  
-   建置 DLL。  
  
 使用僅含資源的 DLL 的應用程式時應該要呼叫 **LoadLibrary** 來[明確連結 DLL](../build/loadlibrary-and-afxloadlibrary.md)。  若要存取資源，請呼叫可以使用在任何類型的資源的 **FindResource** 和 **LoadResource** 泛用函式，或者是呼叫下列資源特定函式的其中之一：  
  
-   `FormatMessage`  
  
-   **LoadAccelerators**  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
 應用程式應該在完成資源使用時呼叫 **FreeLibrary**。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [DELETE\_PENDING\_Editing Resources](http://msdn.microsoft.com/zh-tw/c29d31c7-2d94-40ca-8aa0-c7262883529c)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)