---
title: "管理功能表、控制列和快速鍵 | Microsoft Docs"
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
  - "快速鍵對應表 [C++]"
  - "控制列, 在框架視窗中更新"
  - "框架視窗, 更新"
  - "MDI, 框架視窗"
  - "功能表, 更新為內容變更"
  - "共用功能表"
  - "狀態列, 更新"
  - "更新使用者介面物件"
  - "使用者介面物件, 更新"
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 管理功能表、控制列和快速鍵
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架視窗處理更新使用者介面物件，包括功能表、工具列按鈕、狀態列和快速鍵。  它也會處理共用在 MDI 應用程式的功能表列。  
  
## 處理功能表  
 框架視窗參與更新使用者介面項目使用 [如何更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)中所描述的 `ON_UPDATE_COMMAND_UI` 機制。  在工具列和其他控制項中的按鈕在閒置迴圈期間更新。  在下拉式功能表的功能表項目在功能表列上的功能表之前是更新下拉式清單中。  
  
 對於 MDI 應用程式中， MDI 框架視窗處理功能表列和標題。  MDI 框架視窗擁有使用為功能表列的預設功能表，當沒有現用 MDI 子視窗時。  當沒有使用中的子系時， MDI 框架視窗功能表列由現用 MDI 子視窗的功能表接管。  如果 MDI 應用程式支援多個資料型別，例如圖表工作表和文件、每個型別將它的功能表項目的功能表列和變更主框架視窗的標題。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 提供標準命令提供預設實作會為 MDI 應用程式的 Windows 功能表。  特別是，開新視窗命令 \(**ID\_WINDOW\_NEW**\) 實作建立新的框架視窗與檢視在目前文件。  只有當您需要進階自訂作業，您需要覆寫這些實作。  
  
 相同資料型別的多個 MDI 子視窗共用功能表資源。  如果數個 MDI 子視窗由相同文件樣板建立，它們都使用相同的功能表資源，儲存在 Windows 的系統資源。  
  
## 管理狀態列。  
 框架視窗也會將其工作區內的狀態列和管理狀態列的指示器。  框架視窗清除並更新狀態列的訊息區為需要和顯示提示字元字串，當使用者選取功能表項目或工具列按鈕，如 [如何顯示在狀態列訂單資訊。](../mfc/how-to-display-command-information-in-the-status-bar.md)中所述。  
  
## 處理的快速鍵  
 每個框架視窗維護自動完成您的鍵盤快速鍵轉譯的選擇性快速鍵對應表。  這個機制可讓您輕鬆地定義的快速鍵 \(也稱為快速鍵\) 叫用命令。  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)