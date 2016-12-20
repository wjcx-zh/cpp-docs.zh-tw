---
title: "從類型程式庫加入 MFC 類別 | Microsoft Docs"
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
  - "類別 [C++], 加入 MFC"
  - "MFC, 從類型程式庫加入類別"
  - "類型程式庫, 加入 MFC 類別自"
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從類型程式庫加入 MFC 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用這個精靈從可用型別程式庫中的介面建立 MFC 類別。  您可以將 MFC 類別加入至 [MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控制項](../../mfc/reference/creating-an-mfc-activex-control.md)中。  
  
> [!NOTE]
>  您不必啟用 Automation 建立 MFC 專案，再從型別程式庫加入類別。  
  
 定義方法以及其參數和傳回型別的型別程式庫包含元件所公開之介面的二進位描述。  您必須先登錄型別程式庫，才能在 \[從 Typelib 加入類別精靈\] 的 \[可用的型別程式庫\] 清單中顯示。  如需詳細資訊，請參閱 MSDN Library 中的＜深入探討分散式 COM：型別程式庫和語言整合＞\(英文\)。  
  
### 若要自型別程式庫加入 MFC 類別  
  
1.  在**方案總管**或[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，在您要加入類別的專案名稱上按一下滑鼠右鍵。  
  
2.  在捷徑功能表中，按一下 \[加入\] 後再按一下 \[加入類別\]。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊的 \[樣板\] 窗格中，按一下 \[TypeLib 的 MFC 類別\]，然後按一下 \[開啟\] 以顯示[從 Typelib 加入類別精靈](../../mfc/reference/add-class-from-typelib-wizard.md)。  
  
 在精靈內，您可於型別程式庫中加入一個以上的類別。  同樣地，您可於單一精靈工作階段中自一個以上的型別程式庫加入類別。  
  
 精靈會為每一個從選取之型別程式庫加入的介面，建立一個衍生自 [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md) 的 MFC 類別。  `COleDispatchDriver` 會實作 OLE Automation 的用戶端。  
  
## 請參閱  
 [Automation 用戶端](../../mfc/automation-clients.md)   
 [Automation 用戶端：使用類型程式庫](../../mfc/automation-clients-using-type-libraries.md)