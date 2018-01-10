---
title: "實作介面 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 896ada2c46c68a794265e7344e9b7f7c7f91aebe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-an-interface-visual-c"></a>實作介面 (Visual C++)
若要實作介面，您必須已建立專案做為 ATL COM 應用程式，或包含 ATL 支援的 MFC 應用程式。 您可以使用[ATL 專案精靈](../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[MFC 應用程式中加入 ATL 物件](../mfc/reference/adding-atl-support-to-your-mfc-project.md)實作 MFC 應用程式的 ATL 支援。  
  
 一旦您建立專案，以實作介面，您必須先加入 ATL 物件。 請參閱[將物件和控制項加入 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)精靈，可將物件加入至您的 ATL 專案的清單。  
  
> [!NOTE]
>  精靈不支援 ATL 對話方塊，使用 ATL、 效能物件或效能計數器的 XML Web 服務。  
  
 如果您[加入 ATL 控制項](../atl/reference/adding-an-atl-control.md)，您可以指定是否要實作預設介面，列在[介面](../atl/reference/interfaces-atl-control-wizard.md)該精靈，並在 atlcom.h 中定義的頁面。  
  
 一旦您加入的物件或控制項，您可以實作其他介面，任何可用的型別程式庫中，位於使用實作介面精靈。  
  
 如果您要加入新的介面，您必須將它手動加入專案的.idl 檔案。 請參閱[ATL 專案中加入新的介面](../atl/reference/adding-a-new-interface-in-an-atl-project.md)如需詳細資訊。  
  
### <a name="to-implement-an-interface"></a>若要實作介面  
  
1.  在 類別檢視，以滑鼠右鍵按一下 ATL 物件的類別名稱。  
  
2.  按一下**新增**從捷徑功能表，然後再按一下**實作介面**顯示[實作介面精靈](../ide/implement-interface-wizard.md)。  
  
3.  選取的介面，實作適當的型別程式庫，並按一下**完成**。  
  
4.  在 類別檢視中，展開物件的基底和介面節點以查看您已實作，然後再展開以查看其可用的屬性、 方法和事件的介面節點的介面。  
  
    > [!NOTE]
    >  您也可以使用[物件瀏覽器](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)檢查介面的成員。  
  
## <a name="see-also"></a>請參閱  
 [建立 COM 介面](../ide/creating-a-com-interface-visual-cpp.md)   
 [編輯 COM 介面](../ide/editing-a-com-interface.md)