---
title: 使用程式碼精靈新增功能 (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: 651eac8c630636455dd1ffa04fdd02b71fa3cf62
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509702"
---
# <a name="adding-functionality-with-code-wizards-c"></a>使用程式碼精靈新增功能 (C++)

當您建立專案之後，您會想要變更或新增該專案的功能。 這類工作包括建立新的類別、新增成員函式和變數，以及新增 Automation 方法和屬性。 程式碼精靈的設計目的是為了讓您執行上述所有工作。

> [!NOTE]
> Visual Studio 2019 中已移除下列很少使用的程式碼精靈。 移除這些精靈不會影響 ATL 和 MFC 的一般支援。 這些技術的範例程式碼封存於 Microsoft Docs 和 VCSamples GitHub 存放庫。

- ATL COM+ 1.0 元件精靈
- ATL 動態伺服器網頁元件精靈
- ATL OLE DB 提供者精靈
- ATL 屬性頁精靈
- ATL OLE DB 消費者精靈
- MFC ODBC 消費者
- 來自 ActiveX 控制項的 MFC 類別
- 來自 Type Lib 的 MFC 類別。

> [!NOTE]
> 您可以新增訊息處理常式，並將訊息對應至這些處理常式，並使用 [ [Mfc 類別] Wizard](../mfc/reference/mfc-class-wizard.md)覆寫 mfc 虛擬函式。

## <a name="accessing-c-code-wizards"></a>存取 C++ 程式碼精靈

您可以從下列三個位置存取 [C++ 程式碼精靈]：

- [專案]**** 功能表上的 [新增項目]**** 命令可讓您顯示 `Add New Item` 對話方塊，以協助您新增檔案至專案。 [新增類別]**** 命令會顯示 [[新增類別]](./adding-a-class-visual-cpp.md#add-class-dialog-box) 對話方塊，進而開啟適用於您可以新增至專案之每個類別類型的精靈。 若為 MFC 類別，請使用 [Mfc 類別 Wizard](../mfc/reference/mfc-class-wizard.md)。 [新增資源]**** 命令會顯示 [[新增資源]](../windows/how-to-create-a-resource-script-file.md) 對話方塊，您可以從中建立或選取要新增至專案的資源。

   如果您在 [類別檢視] 中醒目提示專案的類別或介面，[專案]**** 功能表也會顯示下列命令：

  - **實作介面** (僅限來自控制項類別)

  - **新增函數**

  - **加入變數**

  - **連接點** (僅限 ATL 類別)

  - **新增方法** (僅限來自介面)

  - **加入屬性** (僅限來自介面)

  - **新增事件** (僅限來自控制項類別)

- 在 [方案總管]**** 中，以滑鼠右鍵按一下任何資料夾，然後從捷徑功能表按一下 [新增]****，即可讓您將新的或現有的檔案、多個資料夾、項目、類別、資源和 Web 參考新增至專案。

- 從 [[類別檢視] 視窗](/visualstudio/ide/viewing-the-structure-of-code)，以滑鼠右鍵按一下適當的節點，然後從捷徑功能表按一下 [新增]****，即可讓您將函式、變數、類別、屬性、方法、事件、介面、連接點或其他程式碼新增至專案。

   > [!NOTE]
   > Visual Studio 不提供將介面新增至專案的精靈。 您可以藉由使用 [ATL 簡單物件精靈](../atl/reference/atl-simple-object-wizard.md)來新增簡單物件，將介面新增至 ATL 專案或[將 ATL 支援新增至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。 或者，開啟專案的 .idl 檔案，然後鍵入下列程式碼建立介面：

    ```IDL
    interface IMyInterface {
    };
    ```

   如需詳細資訊，請參閱[實作介面](../ide/implementing-an-interface-visual-cpp.md)和[將物件和控制項新增至 ATL 專案](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)。

   |存取程式碼精靈來源|描述|
   |-----------------------------|-----------------|
   |新增項目|「新增項目」程式碼精靈會將原始程式檔新增至您的專案。 如有必要，請建立其他目錄，以包含專案建置引擎預期找到的檔案。 可從新增項目圖示使用的程式碼精靈包括：<br /><br />- 新增 C++ 來源檔案 (.cpp、.h、.idl、.rc、.srf、.def、.rgs)。<br />- 新增網頁程式開發檔案 (.html、.asp、.css、.xml)。<br />- 新增公用程式和資源檔 (.bmp、.cur、.ico、.rct、.sql、.txt)。<br /><br />這些程式碼精靈通常不會要求您提供任何資訊，而是將檔案新增至您的開發樹狀結構。 您可以重新命名屬性視窗中的檔案。|
   |方案總管|可從 [方案總管] 使用的程式碼精靈取決於以滑鼠右鍵按一下項目時的游標焦點所在。 如果當您以滑鼠右鍵按一下項目時未顯示 [新增]**** 選項，請在開發樹狀結構中將游標上移一層，然後再試一次。 不論您的游標所在位置，程式碼精靈一律會將額外的程式碼放在開發樹狀結構中的適當位置。 可從 [方案總管] 使用的程式碼精靈包括：<br /><br />-新增類別 (開啟包含新的程式碼嚮導) 的 [ **加入類別** ] 對話方塊。<br />- 新增資源 (新增、匯入或自訂)。<br />- 新增 Web 參考。|
   |類別檢視|可從 [類別檢視] 使用的程式碼精靈取決於以滑鼠右鍵按一下項目時的游標焦點所在。 如果當您以滑鼠右鍵按一下項目時未顯示 [新增]**** 選項，請在類別樹狀結構中將游標上移一層，然後再試一次。 不論您的游標所在位置，程式碼精靈一律會將額外的程式碼放在開發樹狀結構中的適當位置。 可從 [類別檢視] 使用的程式碼精靈包括：<br /><br />- [新增成員函式](../ide/adding-a-member-function-visual-cpp.md)。<br />- [新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)。<br />- [新增類別](../ide/adding-a-class-visual-cpp.md)。<br />- [實作介面](./implementing-an-interface-visual-cpp.md#implement-interface-wizard) (僅限來自控制項類別)<br />- 只 (ATL 類別[新增連接點](./implementing-a-connection-point-visual-cpp.md#implement-connection-point-wizard)) <br />- [新增方法](./adding-a-method-visual-cpp.md#add-method-wizard) (僅限來自介面)<br />- [加入屬性](./adding-a-property-visual-cpp.md#names-add-property-wizard) (僅限來自介面)<br />- [新增事件](./adding-an-event-visual-cpp.md#add-event-wizard) (僅限來自控制項類別)<br /><br />選取 [新增類別] 會開啟 [新增類別]**** 對話方塊，讓您存取所有新的「新增類別」程式碼精靈。|

## <a name="see-also"></a>另請參閱

[覆寫虛擬函式](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[在 Visual Studio 中巡覽 C++ 程式碼基底](../ide/navigate-code-cpp.md)<br>
[Visual Studio 中的 C++ 專案類型](../build/reference/visual-cpp-project-types.md)<br>
[為 Visual Studio C++ 專案建立的檔案類型](../build/reference/file-types-created-for-visual-cpp-projects.md)
