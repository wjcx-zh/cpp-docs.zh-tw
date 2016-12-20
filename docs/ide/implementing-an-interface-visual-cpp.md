---
title: "實作介面 (Visual C++) | Microsoft Docs"
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
  - "介面, 實作"
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實作介面 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要實作介面，您必須先將專案建立為 ATL COM 應用程式或是包含 ATL 支援的 MFC 應用程式。  您可以使用 [ATL 專案精靈](../atl/reference/atl-project-wizard.md)來建立 ATL 應用程式，或[將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)來為 MFC 應用程式實作 ATL 支援。  
  
 建立專案之後，您就必須先加入 ATL 物件才能實作介面。  如需將物件加入至 ATL 專案的精靈清單，請參閱[將物件和控制項加入至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。  
  
> [!NOTE]
>  精靈不支援 ATL 對話方塊、使用 ATL 的 XML Web Service、效能物件或效能計數器。  
  
 如果[加入 ATL 控制項](../atl/reference/adding-an-atl-control.md)，則您可指定是否要實作列在該精靈的[介面](../atl/reference/interfaces-atl-control-wizard.md)頁面並定義於 atlcom.h 中的預設介面。  
  
 加入物件或控制項之後，您就可以使用實作介面精靈來實作位於任何可用型別程式庫中的其他介面。  
  
 如果要加入新介面，您必須手動將它加入至專案的 .idl 檔。  如需詳細資訊，請參閱[將新介面加入至 ATL 專案](../atl/reference/adding-a-new-interface-in-an-atl-project.md)。  
  
### 若要實作介面  
  
1.  在 \[類別檢視\] 中，以滑鼠右鍵按一下 ATL 物件的類別名稱。  
  
2.  從捷徑功能表按一下 \[加入\]，接著按一下 \[**實作介面**\] 以顯示[實作介面精靈](../ide/implement-interface-wizard.md) \(Implement Interface Wizard\)。  
  
3.  從適當的型別程式庫選取要實作的介面，並按一下 \[完成\]。  
  
4.  在 \[類別檢視\] 中，展開物件的 \[基底和介面\] 節點以檢視您已實作的介面，接著展開介面的節點來檢視可用的屬性、方法及事件。  
  
    > [!NOTE]
    >  您也可使用[物件瀏覽器](http://msdn.microsoft.com/zh-tw/f89acfc5-1152-413d-9f56-3dc16e3f0470)來檢查介面的成員。  
  
## 請參閱  
 [建立 COM 介面](../ide/creating-a-com-interface-visual-cpp.md)   
 [編輯 COM 介面](../ide/editing-a-com-interface.md)