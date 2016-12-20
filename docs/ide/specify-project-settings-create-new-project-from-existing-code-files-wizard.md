---
title: "從現有的程式碼檔建立新專案精靈、指定專案設定 | Microsoft Docs"
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
  - "vc.appwiz.importwiz.appsettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "從現有程式碼檔建立新專案精靈, 專案設定"
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從現有的程式碼檔建立新專案精靈、指定專案設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 \[從現有的程式碼檔建立新專案\] 精靈的這個頁面指定︰  
  
-   新專案的建置環境  
  
-   符合所要產生新專案之特定型別的建置設定  
  
## 工作清單  
 [如何：從現有程式碼建立 C\+\+ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## UIElement 清單  
 **使用 Visual Studio**  
 指定使用 Visual Studio 中包含的建置工具建置新專案。  預設已選取此選項。  
  
 **專案類型**  
 指定精靈將產生的專案類型。  
  
 **Windows 應用程式專案**  
 表示精靈將產生可執行的 Windows 應用程式的專案。  這個選項可從 \[**專案類型**\] 下拉式清單方塊中取得。  
  
 **主控台應用程式專案**  
 表示精靈將產生主控台應用程式的專案。  這個選項可從 \[**專案類型**\] 下拉式清單方塊中取得。  
  
 **動態連結程式庫 \(DLL\) 專案**  
 表示精靈將產生空的動態連結程式庫應用程式的專案。  這個選項可從 \[**專案類型**\] 下拉式清單方塊中取得。  
  
 **靜態程式庫 \(LIB\) 專案**  
 表示精靈將產生靜態程式庫應用程式的專案。  這個選項可從 \[**專案類型**\] 下拉式清單方塊中取得。  
  
 **加入 ATL 的支援**  
 將 ATL 支援加入新專案中。  
  
 **加入 MFC 的支援**  
 將 MFC 支援加入新專案中。  
  
 **加入 Common Language Runtime 的支援**  
 將 CLR 程式設計支援加入新專案中。  
  
 **Common Language Runtime**  
 指定符合 CLR 功能的新專案。  
  
 **Common Language Runtime \(舊語法\)**  
 指定符合 Managed Extensions for C\+\+ 語法的新專案，其為 Visual C\+\+ 2005 之前的 CLR 程式設計語法。  
  
 **使用外部建置系統**  
 指定使用 Visual Studio 中未包含的建置工具建置新專案。  若選取這個選項，即可在 \[**指定偵錯組態設定**\] 和 \[**指定發行組態設定**\] 頁面上指定建置命令列。  
  
> [!NOTE]
>  若核取 \[**使用外部建置系統**\] 選項，IDE 便不會建置新專案，因此編譯時就不需要 \/D、\/I、\/FI、\/AI 或 \/FU 選項。  不過，這些選項必須正確設定，IntelliSense 才能正常運作。  
  
## 請參閱  
 [從現有的程式碼檔建立新專案精靈、指定偵錯組態設定](../ide/specify-debug-configuration-settings.md)   
 [從現有的程式碼檔建立新專案精靈、指定發行組態設定](../ide/specify-release-configuration.md)