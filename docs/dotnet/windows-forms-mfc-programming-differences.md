---
title: "Windows Form/MFC 程式設計的差異 | Microsoft Docs"
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
  - "MFC [C++], Windows Form 支援"
  - "Windows Form [C++], 與 MFC 比較"
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Windows Form/MFC 程式設計的差異
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)中的主題會說明 Windows Form 的 MFC 支援。  如果您還不太熟悉如何使用 .NET Framework 或 MFC 程式設計，這個主題可以為您解說利用這兩者進行程式設計的差異。  
  
 Windows Form 是用於建立以 .NET Framework 為架構的 Microsoft Windows 應用程式。  這個架構提供了先進、物件導向、可擴充的類別集合，讓您可以開發多樣化的 Windows 應用程式。  您可以使用 Windows Form 建立豐富型用戶端應用程式，存取多種類型的資料來源，並提供使用了 Windows Form 控制項的資料顯示和資料編輯工具。  
  
 但是如果您已經熟悉 MFC 的用法，也就能夠以它來建立 Windows Form 尚未明確支援的特定類型應用程式。  Windows Form 應用程式相當於 MFC 對話方塊應用程式。  但是，它們並不提供基礎結構，以便直接支援其他 MFC 應用程式類型，像是 OLE 文件伺服程式\/容器、ActiveX 文件，或是由單一文件介面 \(SDI\)、多重文件介面 \(MDI\) 和多重最上層文件介面 \(MTI\) 的文件\/檢視支援。  您也可以自行編寫邏輯，建立這類應用程式。  
  
 如需 Windows Form 應用程式的詳細資訊，請參閱 [Windows Form 簡介](../Topic/Windows%20Forms%20Overview.md)。  
  
 如需示範 Windows Form 搭配 MFC 使用的範例應用程式，請參閱 [MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en) \(英文\)。  
  
 在 Windows Form 中並沒有和以下所列出的 MFC 檢視、文件和命令傳送相同的功能：  
  
-   Shell 整合  
  
     當您在文件上按一下滑鼠右鍵並且選取像 \[開啟\]、\[編輯\] 或 \[列印\] 等動詞命令時，MFC 就會處理 Shell 所使用的動態資料交換 \(DDE\) 命令和命令列的引數。  Windows Form 並沒有 Shell 整合功能，且不會回應 Shell 動詞命令。  
  
-   文件樣板  
  
     在 MFC 中，文件樣板可以為包含於框架視窗 \(在 MDI、SDI 或 MTI 模式中\) 的檢視和您所開啟的文件建立關聯。  Windows Form 沒有與文件樣板相同的功能。  
  
-   文件  
  
     當文件從 Shell 開啟時，MFC 會登錄文件檔案類型並處理該文件類型。  Windows Form 則不具有文件支援。  
  
-   文件狀態  
  
     MFC 會維持文件的變更狀態。  因此，當您在關閉應用程式、關閉包含應用程式的最後一個檢視，或是從 Windows 結束時，MFC 會提示您需要儲存該文件。  Windows Form 則不具有相同的支援。  
  
-   命令  
  
     MFC 具有命令的概念。  因此，在功能表列、工具列和內容功能表都可以叫用相同的命令，例如 Cut 和 Copy。  在 Windows Form 中，命令與特定 UI 項目 \(例如功能表項目\) 事件會緊密地結合，因此必須明確地連接所有的命令事件。  您也可以使用 Windows Form 中的單一處理常式，處理多重事件。  如需詳細資訊，請參閱[在 Windows Form 中連接多個事件至單一事件處理常式](../Topic/How%20to:%20Connect%20Multiple%20Events%20to%20a%20Single%20Event%20Handler%20in%20Windows%20Forms.md)。  
  
-   命令傳送  
  
     MFC 命令傳送可啟動現用檢視或文件處理命令。  因為相同命令對不同檢視經常具有不同的意義 \(例如 Copy 在文字編輯檢視和圖形編輯器中就表示著不同的行為\)，所以命令必須由現用檢視來處理。  Windows Form 功能表和工具列對現用檢視不具繼承關係，所以要編寫額外的內部程式碼，才可以為 **MenuItem.Click** 事件的每種檢視類型建立不同的處理常式。  
  
-   命令更新機制  
  
     MFC 具有命令更新機制。  因此，現用檢視或文件便決定了 UI 項目的狀態 \(例如，啟用或停用功能表項目、工具列按鈕、核取狀態等等\)。  Windows Form 則不具有相同的命令更新機制。  
  
## 請參閱  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows Forms Walkthroughs](http://msdn.microsoft.com/zh-tw/fd44d13d-4733-416f-aefc-32592e59e5d9)