---
title: 建立 COM 介面
ms.date: 05/14/2019
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 6ad8d50049d34a711937f3d1f73157ce26f69808
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509692"
---
# <a name="create-a-com-interface"></a>建立 COM 介面

Visual Studio 提供精靈與範本來為您的 COM 物件與自動化類別，以建立使用 COM 定義介面和分配介面的專案。

您可以使用這些精靈執行下列三項一般工作：

- [將 ATL 支援新增至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

  當您使用 [ [mfc 應用程式精靈]](../mfc/reference/mfc-application-wizard.md) 建立 mfc 專案，然後執行 [ **將 atl 支援加入至 mfc** 程式碼嚮導] 之後，將 ATL 支援新增至 mfc 應用程式。 這項支援只適用於新增至 MFC 可執行檔或 DLL 專案的簡單 COM 物件。 這些 ATL 物件可以有多個介面。

- [建立 MFC ActiveX 控制項](../mfc/reference/creating-an-mfc-activex-control.md)。

  開啟 [ [MFC ActiveX 控制項建立]](../mfc/reference/mfc-activex-control-wizard.md) ，以建立一個具有產生介面的 ActiveX 控制項，以及 .idl 檔和控制項類別中定義的事件對應。

- [新增 ATL 控制項](../atl/reference/adding-an-atl-control.md)。

  使用 [atl 專案 wizard](../atl/reference/atl-project-wizard.md) 和 [atl control wizard](../atl/reference/atl-control-wizard.md) 的組合來建立 atl ActiveX 控制項。

  您也可以將 ATL 控制項新增至您已新增 ATL 支援的 MFC 專案，如上所述。 此外，如果您在 [新增類別]**** 對話方塊中選取 [ATL 控制項]****，而且您尚未將 ATL 支援新增至 MFC 專案，則 Visual Studio 會顯示對話方塊，確認將 ATL 支援新增至您的 MFC 專案。

  這個精靈會在專案類別中產生 IDL 來源和 COM 對應。

一旦開啟 ATL 專案，[新增類別](./adding-a-class-visual-cpp.md#add-class-dialog-box)對話方塊便可讓您選擇其他精靈和範本，以將 COM 介面新增至您的專案。 下列精靈可讓您建立物件的一或多個介面：

- [ATL COM + 1.0 元件嚮導](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [ATL 簡單物件 wizard](../atl/reference/atl-simple-object-wizard.md)
- [ATL active server page 元件 wizard](../atl/reference/atl-active-server-page-component-wizard.md)
- [ATL 控制項 wizard](../atl/reference/atl-control-wizard.md)

此外，您也可以對 COM 控制項實作新的介面。 只要以滑鼠右鍵按一下 [類別檢視] 中的物件控制項類別，並選擇[實作介面](./implementing-an-interface-visual-cpp.md#implement-interface-wizard)即可。

> [!NOTE]
> Visual Studio 不提供將介面新增至專案的精靈。 您可以藉由使用 [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)來新增簡單物件，將介面新增至 ATL 專案或[將 ATL 支援新增至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。 或者，開啟專案的 .idl 檔案，然後鍵入下列程式碼建立介面：

```
interface IMyInterface {
};
```

如需詳細資訊，請參閱[實作介面](../ide/implementing-an-interface-visual-cpp.md)和[將物件和控制項新增至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。

Visual C++ 提供數種方式來檢視和[編輯為您的專案定義的 COM 介面](#edit-a-com-interface)。 [類別檢視](/visualstudio/ide/viewing-the-structure-of-code)會顯示 C++ 專案的 .idl 檔中定義之任何介面或分配介面的圖示。

對於以 ATL 為基礎的 COM 物件類別，[類別檢視] 會讀取 ATL 類別中的 COM 對應，以顯示 ATL 類別與其實作之任何介面之間的關聯性。

在 [類別檢視] 和其捷徑功能表中，您可以使用介面，如下所示：

- 將 ATL 物件新增至 MFC 為基礎的應用程式。
- 新增方法、屬性和事件。
- 藉由在項目上按兩下，直接跳至項目的介面程式碼。

## <a name="in-this-section"></a>本節內容

- [編輯 COM 介面](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>編輯 COM 介面

您可以使用 [類別檢視] 捷徑功能表中的命令，為 Visual Studio C++ 專案中的 COM 介面定義新方法和屬性。 您也可以從 [工具箱] 為 ActiveX 控制項定義事件。

針對 ATL 和 MFC 型 COM 物件類別，您可以在編輯介面同時編輯類別實作。

> [!NOTE]
> 針對您在 [新增類別]**** 對話方塊外部定義的介面，Visual C++ 會將方法或屬性新增至 .idl 檔案，並將虛設常式新增至實作方法的類別，即使手動新增這些介面時也一樣。

下列三個精靈可協助您自訂現有的介面。 您可以從 [類別檢視] 存取這些介面：

|精靈|專案類型|
|------------|------------------|
|[加入屬性 wizard](./adding-a-property-visual-cpp.md#names-add-property-wizard)|支援 ATL 的 ATL 或 MFC 專案。 以滑鼠右鍵按一下您要新增屬性的介面。<br /><br />Visual C++ 會偵測專案類型，並視需要修改 [新增屬性精靈] 中的選項：<br /><br />-對於使用 [ [MFC 應用程式精靈]](../mfc/reference/mfc-application-wizard.md)建立之專案中的分配介面，叫用 [加入屬性] wizard 會提供 MFC 特定的選項。<br />- 針對 MFC ActiveX 控制項介面，[新增屬性精靈] 會提供內建方法和屬性清單，您可以直接使用或為您的控制項自訂。<br />- 針對所有其他介面，[新增屬性精靈] 會提供大部分情況下都有用的選項。|
|[新增方法 wizard](./adding-a-method-visual-cpp.md#add-method-wizard)|支援 ATL 的 ATL 或 MFC 專案。 以滑鼠右鍵按一下您要新增方法的介面。<br /><br />Visual C++ 會偵測專案類型，並視需要修改 [新增方法精靈] 中的選項：<br /><br />- 針對使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)所建立專案中的分配介面，使用 [新增方法精靈] 會提供 MFC 特定的選項。<br />- 針對 MFC ActiveX 控制項介面，[新增方法精靈] 會提供內建方法和屬性清單，您可以直接使用或為您的控制項自訂。<br />- 針對所有其他介面，[新增方法精靈]**** 會提供大部分情況下都有用的選項。|

此外，您也可以對 COM 控制項實作新的介面。 只要以滑鼠右鍵按一下 [類別檢視] 中的物件控制項類別，並選擇[實作介面](./implementing-an-interface-visual-cpp.md#implement-interface-wizard)即可。
