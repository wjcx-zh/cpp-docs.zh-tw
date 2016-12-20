---
title: "應用程式設定, ATL 專案精靈 | Microsoft Docs"
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
  - "vc.appwiz.atl.com.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案精靈, 應用程式設定"
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 應用程式設定, ATL 專案精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用 ATL 專案精靈的 \[**應用程式設定**\] 頁面來設計基本功能並將其加入至新的 ATL 專案。  
  
## 伺服器類型  
 從下列三種伺服器類型中任選其一：  
  
 **動態連結程式庫 \(DLL\)**  
 選取來建立同處理序伺服程式。  
  
 **可執行檔 \(EXE\)**  
 選取來建立本機跨處理序 \(Out\-Of\-Process\) 伺服程式。  這個選項不允許 MFC 或 COM\+ 1.0 的支援。  也不允許合併 proxy\/stub 程式碼。  
  
 **服務 \(EXE\)**  
 選取來建立當 Windows 啟動時在背景 \(Background\) 執行的 Windows 應用程式。  這個選項不允許 MFC 或 COM\+ 1.0 的支援，也不允許合併 proxy\/stub 程式碼。  
  
## 其他選項  
  
> [!NOTE]
>  所有其他選項都僅供 DLL 專案使用。  
  
 **允許合併 proxy\/stub 程式碼**  
 選取 \[**允許合併 Proxy\/Stub 程式碼**\] 核取方塊，方便您因應處理封送處理 \(Marshaling\) 介面的需求。  這個選項會將 MIDL 產生的 proxy 和 stub 程式碼放置在與伺服器相同的可執行檔中。  
  
 **支援 MFC**  
 選取來指定您的物件包含 MFC 支援。  這個選項會將專案和 MFC 程式庫連結，讓您能夠存取程式庫中包含的任何類別和函式。  
  
 **支援 COM\+ 1.0**  
 選取來修改專案組建 \(Build\) 設定以支援 COM\+ 1.0 元件。  除了標準的程式庫清單之外，精靈還會加入 COM\+ 1.0 元件特定的程式庫 comsvcs.lib。  
  
 除此之外，當啟動應用程式時，mtxex.dll 會延遲載入到主機系統上。  
  
-   \[**支援元件管理員**\] ，如果您的 ATL 專案包含支援的 COM\+ 元件，您可以設定選項。  元件登錄器允許您的 COM\+ 1.0 物件取得元件、登錄元件或未登錄元件的清單 \(一次一個或全部\)。  
  
## 請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)