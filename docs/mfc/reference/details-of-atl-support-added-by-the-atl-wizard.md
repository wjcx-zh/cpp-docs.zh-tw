---
title: "ATL 精靈加入 ATL 支援的詳細資訊 | Microsoft Docs"
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
  - "vc.codewiz.atl.support"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, MFC 專案"
  - "MFC, ATL 支援"
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 精靈加入 ATL 支援的詳細資訊
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您[將 ATL 支援加入至現有的 MFC 可執行檔或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) 時，Visual C\+\+ 會對現有的 MFC 專案進行下列的修改 \(在本範例中，該專案稱為 `MFCEXE`\)：  
  
-   已加入兩個新檔案 \(一個 .idl 檔案和一個 .rgs 檔案，用於登錄伺服器\)。  
  
-   在主應用程式標頭檔 \(Header File\) 和實作檔 \(Implementation File\) \(Mfcexe.h 和 Mfcexe.cpp\) 中，加入新類別 \(衍生自 **CAtlMFCModule**\)。  除了新類別以外，也會將登錄用程式碼加入至 `InitInstance`。  還會將用來撤銷類別物件的程式碼加入至 `ExitInstance` 函式中。  在標頭檔中，最後會在實作檔包含兩個宣告及初始化衍生自 **CAtlMFCModule** 類別 \(Derived class\) 之新 GUID 的標頭檔 \(Initguid.h 和 Mfcexe\_i.c\)。  
  
-   為了要正確登錄伺服器，會有新的 .rgs 檔案加入至專案的資源檔。  
  
## DLL 專案須知  
 當您將 ATL 支援加入至 MFC DLL 專案時，您會看到一些差異。  程式碼被加入 **DLLRegisterServer** 和 **DLLUnregisterServer** 函式來登錄及取消登錄 DLL。  程式碼也會被加入 [DllCanUnloadNow](../Topic/CAtlDllModuleT::DllCanUnloadNow.md) 和 [DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md)。  
  
## 請參閱  
 [MFC 專案中的 ATL 支援](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)