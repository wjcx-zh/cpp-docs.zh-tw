---
title: 將物件和控制項加入至 ATL 專案
ms.date: 05/09/2019
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: b1bf4f85ccf7a0bb2d77bfb96c512349f581f193
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832447"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>將物件和控制項加入至 ATL 專案

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL COM+ 1.0 元件精靈、ATL OLE DB 消費者精靈和 ATL Active Server Page 元件精靈。

您可以使用其中一個 ATL 程式碼精靈，來將物件或控制項加入至 ATL 或 MFC 型專案。 針對您加入的每個 COM 物件或控制項，精靈會產生 .cpp 和 .h 檔案以及 .rgs 檔案來提供指令碼型登錄支援。 Visual Studio 中提供下列 ATL 程式碼精靈：

- [ATL 簡單物件](../../atl/reference/atl-simple-object-wizard.md)
- [ATL 對話方塊](../../atl/reference/atl-dialog-wizard.md)
- [ATL 控制項](../../atl/reference/atl-control-wizard.md)
- [ATL 屬性頁](../../atl/reference/atl-property-page-wizard.md)
- [ATL Active Server Page 元件](../../atl/reference/atl-active-server-page-component-wizard.md)
- [ATL OLE DB 消費者](../../atl/reference/atl-ole-db-consumer-wizard.md)
- [將 ATL 支援加入 MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)
- [ATL COM+ 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [ATL OLE DB 提供者](../../atl/reference/atl-ole-db-provider-wizard.md)

> [!NOTE]
> 將 ATL 物件加入至專案之前，您應該先在其相關說明主題中檢閱該物件的詳細資訊和需求。

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>使用 ATL 控制項精靈加入物件或控制項

1. 在 [方案總管]**** 中，以滑鼠右鍵按一下專案節點，然後從捷徑功能表中按一下 [加入]****。 按一下 [加入類別]****。

   [[加入類別](../../ide/add-class-dialog-box.md)] 對話方塊隨即出現。

1. 透過在 [類別]**** 窗格中選取的 **ATL** 資料夾，從 [範本]**** 窗格中選取要插入的物件。 按一下 [開啟]。 適用於所選取物件的程式碼精靈隨即出現。

   > [!NOTE]
   > 如果您想要將 ATL 物件加入至 MFC 專案，您必須將 ATL 支援加入至現有的專案。 您可以依照[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)中的指示來執行此動作。

   或者，如果您在未事先加入 ATL 支援的情況下，嘗試將 ATL 物件加入至 MFC 專案，則 Visual Studio 會提示您指定是否要將 ATL 支援加入至專案。 按一下 [是]**** 以將 ATL 支援加入至專案，並開啟所選取的 ATL 精靈。

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio 中的 C++ 專案類型](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 執行時間程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[預設 ATL 專案設定](../../atl/reference/default-atl-project-configurations.md)
