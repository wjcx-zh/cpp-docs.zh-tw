---
title: "加入 ATL OLE DB 消費者 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL OLE DB 消費者"
  - "ATL 專案, 加入 ATL OLE DB 消費者"
  - "OLE DB, 在專案中加入 ATL OLE DB 消費者"
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入 ATL OLE DB 消費者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用這個精靈來將 ATL OLE DB 消費者加入至專案。  ATL OLE DB 消費者是由 OLE DB 存取子 \(Accessor\) 類別和存取資料來源所需的資料繫結 \(Data Binding\) 所組成。  專案必須是建立為 ATL COM 應用程式，或是包含 ATL 支援 \(ATL OLE DB 消費者精靈會自動加入\) 的 MFC 或 Win32 應用程式。  
  
 您可以**Note** 加入 OLE DB 消費者加入至 MFC 專案。  如果您要這樣做，ATL OLE DB 消費者精靈會將需要的 COM 支援加入至您的專案中。  這是假設您在建立該 MFC 專案時，選取了預設選取的 \[**ActiveX 控制項**\] 核取方塊 \(位於 MFC 專案應用程式精靈的 \[**進階功能**\] 頁面\)。  選取這個選項可以確保該應用程式會呼叫 **CoInitialize** 和 **CoUninitialize**。  如果您在建立 MFC 專案時沒有選取 \[**ActiveX 控制項**\]，必須在主程式碼中呼叫 **CoInitialize** 和 **CoUninitialize**。  
  
### 若要將 ATL OLE DB 消費者加入至您的專案  
  
1.  在 \[類別檢視\] 中以滑鼠右鍵按一下專案。  在捷徑功能表中，按一下 \[加入\]，然後再按一下 \[加入類別\]。  
  
2.  在 Visual C\+\+ 資料夾中，按兩下 \[ATL OLE DB 消費者\] 圖示，或選取它再按一下 \[開啟\]。  
  
     接著會開啟 ATL OLE DB 消費者精靈。  
  
3.  定義 [ATL OLE DB 消費者精靈](../../atl/reference/atl-ole-db-consumer-wizard.md)所描述的設定。  
  
4.  按一下 \[**完成**\] 關閉精靈。  剛建立的 OLE DB 消費者程式碼將會插入您的專案中。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)