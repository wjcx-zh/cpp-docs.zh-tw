---
title: 將物件和控制項新增至 ATL 專案
ms.date: 11/04/2016
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
ms.openlocfilehash: d16e9a9e7b92d2a98f8994227c5641994677fdda
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221216"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>將物件和控制項新增至 ATL 專案

您可以使用其中一個 ATL 程式碼精靈加入 ATL 或 MFC 為基礎的專案中的物件或控制項。 針對每個 COM 物件或控制項您加入，亦即，精靈會產生.cpp 和.h 檔案，以及指令碼為基礎的登錄支援.rgs 檔案。 在 Visual Studio 中有下列的 ATL 程式碼精靈：

||||
|-|-|-|
|[ATL 簡單物件](../../atl/reference/atl-simple-object-wizard.md)|[ATL 對話方塊](../../atl/reference/atl-dialog-wizard.md)|[ATL 控制項](../../atl/reference/atl-control-wizard.md)|
|[ATL 屬性頁](../../atl/reference/atl-property-page-wizard.md)|[ATL Active Server Page 元件](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL OLE DB 消費者](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[將 ATL 支援加入 MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM+ 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[ATL OLE DB 提供者](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> 然後再將 ATL 物件新增至您的專案，您應該檢閱的詳細資訊和需求的相關說明主題中的物件。

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>若要加入物件或控制項，使用 ATL 控制項精靈

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下專案節點，然後按一下**新增**從捷徑功能表。 按一下 **加入類別**。

   [加入類別](../../ide/add-class-dialog-box.md) 對話方塊隨即出現。

1. 具有**ATL**中所選取的資料夾**類別**窗格中，選取要從 插入物件**範本**窗格。 按一下 [開啟]。 在所選物件的程式碼精靈隨即出現。

   > [!NOTE]
   > 如果您想要將 ATL 物件加入至 MFC 專案，您必須加入 ATL 支援加入現有的專案。 您可以依照下列中的指示[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

   或者，如果您嘗試加入 MFC 專案中的 ATL 物件，而不需先前新增 ATL 支援時，Visual Studio 會提示您指定是否要讓 ATL 支援加入至專案。 按一下 **是**將 ATL 支援加入至專案，並開啟所選的 ATL 精靈。

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[C++在 Visual Studio 中的專案類型](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)
