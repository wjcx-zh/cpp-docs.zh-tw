---
title: "加入 ATL 屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 加入屬性頁"
  - "控制項 [ATL], 屬性頁"
  - "屬性頁, 加入"
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 加入 ATL 屬性頁
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要將 Active Template Library \(ATL\) 屬性頁加入至專案，您必須先將專案建立為 ATL 應用程式或包含 ATL 支援的 MFC 應用程式。  您可以使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[將 ATL 物件加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)以實作 MFC 應用程式的 ATL 支援。  
  
 如果要加入控制項的屬性頁，則控制項必須支援 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 介面。  依照預設，當您使用 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)[建立 ATL 控制項](../../atl/reference/adding-an-atl-control.md)時，這個介面是在控制項類別的衍生清單中。  
  
> [!NOTE]
>  如果 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 不在控制項類別的衍生清單中，您就必須手動將它加入。  
  
### 若要將 ATL 屬性頁加入至您的專案  
  
1.  在 \[**方案總管**\] 或[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，在要加入 ATL 屬性頁的專案名稱上按一下滑鼠右鍵。  
  
2.  在捷徑功能表中，按一下 \[加入\] 後再按一下 \[加入類別\]。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊的 \[樣板\] 窗格中，按一下 \[ATL 屬性頁\]，然後按一下 \[開啟\] 以顯示 [ATL 屬性頁精靈](../../atl/reference/atl-property-page-wizard.md)。  
  
 一旦為控制項建立了屬性頁，您就必須在控制項的屬性對應中提供 [PROP\_PAGE](../Topic/PROP_PAGE.md) 項目。  
  
## 請參閱  
 [屬性頁](../../atl/atl-com-property-pages.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [Example: Implementing a Property Page](../../atl/example-implementing-a-property-page.md)