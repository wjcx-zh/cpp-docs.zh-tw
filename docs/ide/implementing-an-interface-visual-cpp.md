---
title: 實作介面 (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- interfaces, implementing
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 5146a8ced1b8347ea724940a7419d8d2507b5b58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449643"
---
# <a name="implementing-an-interface-visual-c"></a>實作介面 (Visual C++)

若要實作介面，您必須已將專案建立作為 ATL COM 應用程式，或作為包含 ATL 支援的 MFC 應用程式。 您可以使用 [ATL 專案精靈](../atl/reference/atl-project-wizard.md)建立 ATL 應用程式，或[將 ALT 物件新增至 MFC 應用程式](../mfc/reference/adding-atl-support-to-your-mfc-project.md)，以實作 MFC 應用程式的 ATL 支援。

建立專案之後，若要實作介面，您必須先新增 ATL 物件。 請參閱[將物件和控制項新增至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)，以取得將物件新增至 ATL 專案的清單。

> [!NOTE]
>  精靈不支援 ATL 對話方塊、使用 ATL 的 XML Web 服務、效能物件或效能計數器。

如果您[新增 ATL 控制項](../atl/reference/adding-an-atl-control.md)，您可以指定是否要實作預設介面，預設介面列在該精靈的[介面](../atl/reference/interfaces-atl-control-wizard.md) 頁面，並定義在 atlcom.h 中。

一旦您新增物件或控制項，便可以使用 [實作介面精靈] 實作其他介面，介面位於任何可用的型別程式庫中。

如果您要新增介面，必須將它手動新增至專案的 .idl 檔案。 請參閱[在 ATL 專案中新增介面](../atl/reference/adding-a-new-interface-in-an-atl-project.md)，以取得詳細資訊。

### <a name="to-implement-an-interface"></a>實作介面

1. 在 [類別檢視] 中，以滑鼠右鍵按一下 ATL 物件的類別名稱。

1. 從捷徑功能表按一下 [新增]，然後按一下 [實作介面] 以顯示[實作介面精靈](../ide/implement-interface-wizard.md)。

1. 從適當的型別程式庫選取要實作的介面，然後按一下 [完成]。

1. 在 [類別檢視] 中，展開物件的 [基底] 和 [介面] 節點以查看您已實作的介面，然後展開介面的節點以查看其可用的屬性、方法和事件。

   > [!NOTE]
   > 您也可以使用[物件瀏覽器](/visualstudio/ide/viewing-the-structure-of-code)來檢查介面的成員。

## <a name="see-also"></a>請參閱

[建立 COM 介面](../ide/creating-a-com-interface-visual-cpp.md)<br>
[編輯 COM 介面](../ide/editing-a-com-interface.md)