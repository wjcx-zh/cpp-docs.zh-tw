---
title: 新增 ATL 屬性頁
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 4cd7444d18d26124f8c3c642bba55fb7592f5c8b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499321"
---
# <a name="adding-an-atl-property-page"></a>新增 ATL 屬性頁

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL 屬性頁精靈。

若要將 Active Template Library (ATL) 屬性頁新增至您的專案中，您的專案必須已經建立為 ATL 應用程式，或含有 ATL 支援的 MFC 應用程式。 您可以使用 [ [Atl 專案嚮導]](../../atl/reference/atl-project-wizard.md) 來建立 atl 應用程式，或 [將 atl 物件加入至 mfc 應用](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) 程式，以執行 MFC 應用程式的 atl 支援。

如果您要新增某個控制項的屬性頁，您的控制項必須支援 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 介面。 根據預設，當您使用 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)[建立 ATL 控制項](../../atl/reference/adding-an-atl-control.md)時，此介面位於您控制項類別的衍生清單中。

> [!NOTE]
> 如果您的控制項類別在其衍生清單中沒有 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)，您必須手動新增。

## <a name="to-add-an-atl-property-page-to-your-project"></a>若要將 ATL 屬性頁新增至您的專案

1. 在 [方案總管]**** 或 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code) 中，以滑鼠右鍵按一下您要在其中新增 ALT 屬性頁之專案的名稱。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入類別**]。

1. 在 [加入類別]](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 對話方塊的 [範本]**** 窗格中，按一下 [ATL 屬性頁]****，然後按一下 [開啟]**** 以顯示 [ATL 屬性頁精靈](../../atl/reference/atl-property-page-wizard.md)。

一旦您建立某個控制項的屬性頁之後，您必須在該控制項的屬性對應中提供 [PROP_PAGE](property-map-macros.md#prop_page) 項目。

## <a name="see-also"></a>另請參閱

[屬性頁](../../atl/atl-com-property-pages.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[範例：執行屬性頁](../../atl/example-implementing-a-property-page.md)
