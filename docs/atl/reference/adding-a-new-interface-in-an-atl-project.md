---
title: 在 ATL 專案中新增介面
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 8bf0138f85929e06b67e9a2e294eda8a2f385e1a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499380"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>在 ATL 專案中新增介面

當您將介面加入至物件或控制項時，您會為該介面中的每個方法建立 stub 時函數。 在您的物件或控制項中，您只能新增目前在現有類型程式庫中找到的介面。 此外，您加入介面的類別必須執行 [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) 宏，或者，如果專案是屬性，則必須具有 `coclass` 屬性。

您可以使用下列兩種方式之一，將新介面加入至控制項：在類別檢視中手動或使用程式碼嚮導。

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>使用類別檢視中的程式碼嚮導，將介面新增至現有的物件或控制項

1. 在 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下控制項的類別名稱。 例如，完整控制項或複合控制項，或任何其他在其標頭檔中執行 BEGIN_COM_MAP 宏的控制項類別。

1. 在快捷方式功能表上，按一下 [ **加入**]，然後按一下 [ **執行介面**]。

1. 在 [ [執行介面嚮導]](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard)中選取要執行的介面。 如果介面不存在於任何可用的 typelib 中，則您必須手動將它加入至 .idl 檔。

## <a name="to-add-a-new-interface-manually"></a>手動新增介面

1. 將新介面的定義加入 .idl 檔。

1. 從介面衍生您的物件或控制項。

1. 為介面建立新的 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ，或者，如果專案是屬性，請加入 `coclass` 屬性。

1. 在介面上執行方法。

## <a name="see-also"></a>另請參閱

[ATL 專案精靈](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio 中的 C++ 專案類型](../../build/reference/visual-cpp-project-types.md)<br/>
[使用 ATL 和 C 執行時間程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[預設 ATL 專案設定](../../atl/reference/default-atl-project-configurations.md)
