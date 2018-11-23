---
title: 實作介面
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 8e166f806d247cd93ff0f471360d749fa95e430b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692897"
---
# <a name="implement-an-interface"></a>實作介面

若要實作介面，您必須已將專案建立作為 ATL COM 應用程式，或作為包含 ATL 支援的 MFC 應用程式。 您可以使用 [[ATL 專案精靈]](../atl/reference/atl-project-wizard.md) 建立 ATL 應用程式，或使用 [[將 ALT 物件新增至 MFC 應用程式]](../mfc/reference/adding-atl-support-to-your-mfc-project.md)，來實作 MFC 應用程式的 ATL 支援。

建立專案之後，若要實作介面，您必須先新增 ATL 物件。 如需將物件新增至 ATL 專案的精靈清單，請參閱[將物件和控制項新增至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。

> [!NOTE]
> 精靈不支援 ATL 對話方塊、使用 ATL 的 XML Web 服務、效能物件或效能計數器。

若您[新增 ATL 控制項](../atl/reference/adding-an-atl-control.md)，可指定是否要實作預設介面。 預設介面列於該精靈的 [[介面]](../atl/reference/interfaces-atl-control-wizard.md) 頁面上，並定義於 atlcom.h 中。

在您新增了物件或控制項後，可使用 [實作介面精靈] 實作位於任何可用型別程式庫中的其他介面。

若要新增介面，您必須將它手動新增至專案的 .idl 檔案。 如需詳細資訊，請參閱[在 ATL 專案中新增介面](../atl/reference/adding-a-new-interface-in-an-atl-project.md)。

**實作介面：**

1. 在 [類別檢視] 中，以滑鼠右鍵按一下 ATL 物件的類別名稱。

1. 從捷徑功能表選擇 [新增]，然後選擇 [實作介面]，以顯示 [[實作介面精靈]](#implement-interface-wizard)。

1. 從適當的型別程式庫選取要實作的介面，然後選取 [完成]。

1. 在 [類別檢視] 中，展開物件的 [基底] 及 [介面] 節點，以查看已實作的介面。 然後展開介面的節點，以查看其可用屬性、方法及事件。

   > [!NOTE]
   > 您也可以使用 [[物件瀏覽器]](/visualstudio/ide/viewing-the-structure-of-code) 檢查介面的成員。

## <a name="in-this-section"></a>本節內容

- [實作介面精靈](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>實作介面精靈

這個精靈將實作 COM 物件的介面。 許多介面的實作會包含在 Visual Studio 和 Windows 所提供的 COM 程式庫中。 當物件的執行個體建立以後，介面實作會與該物件建立關聯。 它也會提供物件所提供的服務。

如需討論介面和實作的資訊，請參閱 Windows SDK 中的 [Interfaces and interface implementations](/windows/desktop/com/interfaces-and-interface-implementations) (介面和介面實作)。

- **實作介面來源**

  指定從中建立介面之型別程式庫的位置。

  |選項|描述|
  |------------|-----------------|
  |**Project**|型別程式庫是專案的一部分。|
  |**Registry**|型別程式庫會在系統中註冊。 已註冊的型別程式庫會列於 [可用的型別程式庫] 中。|
  |**檔案**|型別程式庫不一定會在系統中註冊，但會包含在檔案中。 在 [位置] 中提供檔案位置。|

- **可用的型別程式庫**

  顯示含有您可實作之介面定義的可用型別程式庫。 若您在 [實作介面來源] 下選擇 [檔案]，就無法變更此方塊。

- **位置**

  顯示 [可用的型別程式庫] 清單中目前選取之型別程式庫的位置。 若您已在 [實作介面來源] 下選取 [檔案]，請選取省略符號按鈕，以找出含有要使用之型別程式庫的檔案。

- **介面**

  顯示定義包含在目前於 [可用型別程式庫] 方塊中選取之型別程式庫內的介面。

  > [!NOTE]
  > 介面若與所選物件已執行的介面同名，就不會顯示在 [介面] 方塊中。

  |傳輸按鈕|描述|
  |---------------------|-----------------|
  |**>**|將 [介面] 清單中目前選取的介面名稱新增至 [實作介面] 清單。|
  |**>>**|將 [介面] 清單中所有可用介面名稱新增至 [實作介面] 清單。|
  |**\<**|移除 [實作介面] 清單中目前選取的介面名稱。|
  |**\<\<**|移除 [實作介面] 清單中目前列出的所有介面名稱。|

- **實作介面**

  顯示您已經選取要在物件上實作的介面名稱。

  > [!NOTE]
  > 若您包含多個衍生自 `IDispatch` 的介面，或者若要嘗試實作衍生自類別中其他介面的介面，則您必須區分 COM_MAP 項目。 如需詳細資訊，請參閱 [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2)。
