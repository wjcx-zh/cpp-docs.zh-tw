---
title: 表單檢視 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 94d8b7d026ee3aaf1bac9dee2226de6dd9382599
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615687"
---
# <a name="form-views-mfc"></a>表單檢視 (MFC)

您可以將表單新增至支援 MFC 程式庫的任何 Visual C++ 應用程式，包括以[表單為基礎的應用程式](reference/creating-a-forms-based-mfc-application.md)（其 view 類別衍生自其中一個 `CFormView` ）。 如果您最初沒有建立應用程式來支援表單，Visual C++ 會在您插入新表單時為您新增這種支援。 在執行預設檔[/視圖架構](document-view-architecture.md)的 SDI 或 MDI 應用程式中，當使用者選擇**新**的命令時（預設會在 [檔案]**功能表上**），Visual C++ 會提示使用者從可用的表單中進行選擇。

使用 SDI 應用程式時，當使用者選擇**新**的命令時，表單的目前實例會繼續執行，但如果找不到，則會建立具有所選表單的應用程式的新實例。 在 MDI 應用程式中，當使用者選擇**新**的命令時，表單的目前實例會繼續執行。

> [!NOTE]
> 您可以將表單插入對話方塊架構應用程式中（其對話方塊類別是以為基礎 `CDialog` ，另一個則不會實作為 view 類別）。 不過，如果沒有**檔**/視圖架構，Visual C++ 不會自動&#124;**新**功能來執行檔案。 您必須建立一個方法，讓使用者能夠查看其他表單，例如，藉由使用各種屬性頁來執行索引標籤式對話方塊。

當您將新的表單插入應用程式時，Visual C++ 會執行下列動作：

- 根據您選擇的其中一個表單樣式類別，建立類別（、、 `CFormView` `CRecordView` `CDaoRecordView` 或 `CDialog` ）。

- 建立具有適當樣式的對話方塊資源（或者，您可以使用尚未與類別相關聯的現有對話資源）。

   如果您選擇現有的對話資源，您可能需要使用對話方塊的 [屬性] 頁面來設定這些樣式。 對話方塊的樣式必須包括：

     **WS_CHILD**= 開啟

     **WS_BORDER**= 關閉

     **WS_VISIBLE**= 關閉

     **WS_CAPTION**= 關閉

針對以檔/視圖架構為基礎的應用程式，**新的表單**命令（以滑鼠右鍵按一下類別檢視）也會：

- 建立以為 `CDocument` 基礎的類別

   您可以使用專案中任何現有的類別，而不是建立新的類別 `CDocument` 。

- `CDocument`使用字串、功能表和圖示資源，產生檔範本（衍生自）。

   您也可以建立用來做為範本基礎的新類別。

- `AddDocumentTemplate`在應用程式的程式碼中新增對的呼叫 `InitInstance` 。

   Visual C++ 會為您所建立的每個新表單加入此程式碼，當使用者選擇**新**的命令時，會將表單新增至可用的表單清單。 這段程式碼包括表單的相關聯資源識別碼，以及相關聯的檔、視圖和框架類別的名稱，它們會組成新的表單物件。

   檔範本可做為檔、框架視窗和 views 之間的連接。 針對單一檔，您可以建立許多範本。

如需詳細資訊，請參閱：

- [建立以表單為基礎的應用程式](reference/creating-a-forms-based-mfc-application.md)

- [將表單插入專案中](inserting-a-form-into-a-project.md)

## <a name="see-also"></a>另請參閱

[使用者介面元素](user-interface-elements-mfc.md)
