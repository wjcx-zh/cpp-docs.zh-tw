---
title: 加入 ATL 屬性頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c84cdabddb96d2deeecd09f26101e37d9c99d0ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357065"
---
# <a name="adding-an-atl-property-page"></a>加入 ATL 屬性頁
Active Template Library (ATL) 屬性頁加入您的專案，您的專案必須已建立以 ATL 應用程式，或包含 ATL 支援的 MFC 應用程式。 您可以使用[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)建立 ATL 應用程式或[MFC 應用程式中加入 ATL 物件](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)實作 MFC 應用程式的 ATL 支援。  
  
 如果您要加入的控制項屬性頁，您的控制項必須支援[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)介面。 根據預設，這個介面是在衍生清單控制項的類別時您[建立 ATL 控制項](../../atl/reference/adding-an-atl-control.md)使用[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)。  
  
> [!NOTE]
>  如果您的控制項類別並沒有[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)其衍生在清單中，您必須手動加入。  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>將 ATL 屬性頁新增至您的專案  
  
1.  在**方案總管 中**或[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下您要加入 ATL 屬性頁的專案名稱。  
  
2.  從捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊，在 [範本] 窗格中，按一下**ATL 屬性頁**，然後按一下 **開啟**顯示[ATL屬性頁精靈](../../atl/reference/atl-property-page-wizard.md).  
  
 一旦您建立控制項的屬性頁，您必須提供[PROP_PAGE](property-map-macros.md#prop_page)控制項的屬性對應中的項目。  
  
## <a name="see-also"></a>另請參閱  
 [屬性頁](../../atl/atl-com-property-pages.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [範例︰實作屬性頁](../../atl/example-implementing-a-property-page.md)

