---
title: 新增 ATL 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: fac1efeb3d373a8324828a8b10f0570f253f6103
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499294"
---
# <a name="adding-an-atl-control"></a>新增 ATL 控制項

您可以使用此嚮導，將使用者介面物件加入至支援所有可能容器之介面的專案。 若要支援這些介面，專案必須已經建立為 ATL 應用程式，或作為包含 ATL 支援的 MFC 應用程式。 您可以使用 [ [ATL 專案嚮導]](../../atl/reference/atl-project-wizard.md) 來建立 atl 應用程式，或 [將 atl 物件加入至 mfc 應用](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) 程式，以執行 MFC 應用程式的 atl 支援。

## <a name="to-add-an-atl-control-to-your-project"></a>將 ATL 控制項新增至專案

1. 在 **方案總管** 或 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下您要新增 ATL 簡單物件的專案名稱。

1. 從快捷方式功能表按一下 [ **新增** ]，然後按一下 [ **加入類別**]。

1. 在 [ [加入類別](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) ] 對話方塊的 [範本] 窗格中，按一下 [ **atl 控制項**]，然後按一下 [ **加入** ] 以顯示 [ATL 控制項 Wizard](../../atl/reference/atl-control-wizard.md)。

您可以使用 **ATL 控制項嚮導**來建立三種控制項類型中的其中一種：

- 標準控制項

- 複合控制項

- DHTML 控制項

此外，您可以在嚮導的 [**選項**] 頁面上選取 [**最小控制權**]，減少控制項的大小，並移除大部分容器未使用的介面。

## <a name="see-also"></a>另請參閱

[將功能新增至複合控制項](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)
