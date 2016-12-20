---
title: "OLE 控制項類別 | Microsoft Docs"
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
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 類別 [C++]"
  - "ActiveX 控制項類別 [C++]"
  - "ActiveX 控制項 [C++], OLE 控制項類別"
  - "自訂控制項 [MFC], 類別"
  - "OLE 控制項類別 [C++]"
  - "OLE 控制項 [C++], 類別"
  - "可重複使用的元件類別"
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 控制項類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些是您使用在撰寫 OLE automation 控制項的主要類別。  在 OLE automation 控制項模組的 `COleControlModule` 類別與應用程式的 [CWinApp](../mfc/reference/cwinapp-class.md) 類別。  每個模組實作一個或多個 OLE automation 控制項;這些控制項由 `COleControl` 物件表示。  使用 `CConnectionPoint` 物件，這些控制項與其容器通訊。  
  
 而 `COlePropertyPage` 和 `CPropExchange` 類別可協助您實作屬性頁和屬性設定為您的控制項， `CPictureHolder` 和 `CFontHolder` 類別會封裝圖片和字型的 COM 介面。  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 取代您的 OLE automation 控制項模組的 `CWinApp` 類別。  衍生自 `COleControlModule` 類別開發 OLE automation 控制項模組物件。  它為初始化的 OLE automation 控制項模型提供成員函式。  
  
 [COleControl](../mfc/reference/colecontrol-class.md)  
 衍生自 `COleControl` 類別開發 OLE automation 控制項。  衍生自 `CWnd`，這個類別繼承自 Windows 視窗物件的所有功能以及其他 OLE 特定功能，例如事件引發和支援的方法和屬性。  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 `CConnectionPoint`類別定義用來與其他 OLE 物件通訊的特殊介面類型，稱為「連接點」。  連接點實作可以啟始對其他物件的動作，例如引發事件和變更告知的輸出介面。  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 封裝 Windows 圖片物件和 `IPicture` COM 介面的功能;用來實作 OLE automation 控制項的自訂圖片屬性。  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 封裝 Windows 字型物件和 `IFont` COM 介面的功能，並實作OLE控制的內建字型屬性。  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 用來將OLE控制項的屬性顯示在類似對話方塊的圖形介面中。  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 支援 OLE 控制項的屬性永續性實作。  類似於對話方塊的 [CDataExchange](../mfc/reference/cdataexchange-class.md) 。  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 取得 moniker 或者成為 moniker 的字串表示以及繫結進行同步處理的 Moniker 是一個資料流。  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 類似於 `CMonikerFile`工作;不過，其所繫結之非同步 Moniker 是一個資料流。  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 實作可以非同步載入的 OLE 控制項屬性。  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 實作非同步傳輸且在記憶體檔案中快取的 OLE 控制項屬性。  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 允許現用文件接收來自其容器的使用者介面的命令 \(例如 FileNew，開啟，列印，等等\)，並允許容器接收來自現用文件的使用者介面的命令。  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 用來處理任意類型和維度的陣列。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)