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
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365304"
---
# <a name="form-views-mfc"></a>表單檢視 (MFC)

您可以將表單添加到支援 MFC 函式庫的任何 Visual C++ 應用程式,包括[基於窗體的應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)`CFormView`(其檢視類派生自的應用程式)。 如果您最初未創建應用程式以支援表單,則 Visual C++將在插入新窗體時添加此支援。 在 SDI 或 MDI 應用程式中,當使用者選擇**New**命令(預設情況下,在 **'檔案"** 選單上)[時,Visual](../mfc/document-view-architecture.md)C++提示使用者從可用表單中進行選擇。

使用 SDI 應用程式時,當使用者選擇**New**命令時,窗體的當前實例將繼續運行,但如果找不到選定窗體,則將創建具有所選窗體的應用程式的新實例。 在 MDI 應用程式中,當使用者選擇**New**命令時,窗體的當前實例將繼續運行。

> [!NOTE]
> 您可以將表單插入到基於對話框的應用程式(其對話框類基於`CDialog`的,並且沒有實現視圖類的應用程式)。 但是,如果沒有文檔/檢視體系結構,Visual C++不會自動實現 **「檔**&#124;**新功能**。 您必須創建一種方法,以便使用者查看其他窗體,例如,通過實現具有各種屬性頁的選項卡式對話方塊。

將新表單插入到應用程式中時,Visual C++ 執行以下操作:

- 以您選擇的表單樣式類之一`CFormView`(、`CRecordView``CDaoRecordView``CDialog`或) 建立類。

- 創建具有適當樣式的對話方塊資源(或者可以使用尚未與類關聯的現有對話框資源)。

   如果選擇現有對話框資源,則可能需要使用對話框的"屬性"頁來設置這些樣式。 對話框的樣式必須包括:

     **WS_CHILD**= 開啟

     **WS_BORDER**= 關閉

     **WS_VISIBLE**= 關閉

     **WS_CAPTION**= 關閉

對於基於文件/檢視體系結構的應用程式 **,「新建窗體」** 命令(在類檢視中右鍵單擊)也:

- 建立`CDocument`的類別

   您可以在專案中使用任何基於的現有`CDocument`類,而不是創建新類。

- 使用字串、功能表和圖示資源`CDocument`生成文檔範本(派生自)。

   您還可以創建一個新類,以基於該範本。

- 在應用程式`AddDocumentTemplate``InitInstance`的代碼中添加調用。

   Visual C++為建立的每個新窗體添加此代碼,當使用者選擇 **"新建"** 命令時,該表單將表單添加到可用表單清單中。 此代碼包括窗體的關聯資源 ID 以及組成新窗體物件的關聯文件、視圖和框架類的名稱。

   文件範本用作文檔、框架視窗和視圖之間的連接。 對於單個文件,您可以創建許多範本。

如需詳細資訊，請參閱

- [建立表單的應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [將表單插入專案中](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)
