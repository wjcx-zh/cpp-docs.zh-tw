---
title: HOW TO：包含資源在編譯時期 （c + +）
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 06ad2f90e7e72492f1e6ca4000a6c101fc36b205
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320662"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>HOW TO：包含資源在編譯時期 （c + +）

通常它是簡單且方便使用一個資源指令碼 (.rc) 檔中的所有資源的預設排列方式。 不過，有幾個原因會放置在主要.rc 檔以外的檔案中的資源：

- 若要儲存.rc 檔時不會刪除的資源陳述式中加入註解。

   資源編輯器不直接讀取.rc 或`resource.h`檔案。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 正常編譯處理程序，在編譯程序期間會捨棄未符號 （例如，註解） 的資訊。 每當.aps 檔未與.rc 檔取得同步的都會重新產生.rc 檔案 (例如，當您儲存時，資源編輯器會覆寫.rc 檔和`resource.h`檔案)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。

- 若要包含已完成開發及測試的資源，而且不需要進一步修改。 （任何包含但不含.rc 副檔名的檔案不是由資源編輯器可編輯）。

- 若要包含的資源正在使用由數個不同的專案，或屬於原始程式碼版本控制系統，因此必須有中央位置，讓修改影響所有專案。

- 為了包含自訂格式的資源 (例如 RCDATA 資源)。 RCDATA 資源可能會有特殊需求。 比方說，您不能使用做為值的運算式，為 nameID 欄位。 如需詳細資訊，請參閱 Windows SDK 文件。

## <a name="resource-includes"></a>資源包含

您可以將資源其他檔案中加入目前的專案在編譯時期藉由列出在**編譯時間指示詞**方塊中**Resource Includes**  對話方塊。

如果您將區段在現有的.rc 檔符合下列任一條件時，您應該將該區段置於一或多個個別.rc 檔，並將它們包含在專案中使用**Resource Includes**  對話方塊。 *Projectname*.rc2 檔建立新專案的 \res 子目錄中用於此目的。

您可以使用**Resource Includes**對話方塊中，在 c + + 專案中，修改儲存專案.rc 檔和所有中的所有資源的環境的一般工作安排[符號](../windows/symbols-resource-identifiers.md)Resource.h 中。

若要開啟 [ **Resource Includes** ] 對話方塊中，以滑鼠右鍵按一下.rc 檔案中[資源檢視](../windows/resource-view-window.md)，然後選擇**Resource Includes**從捷徑功能表。 請參閱下列內容：

|屬性|描述|
|--|----|
|**符號標頭檔**|可讓您變更標頭檔的名稱，您的資源的符號定義就是儲存在這個標頭檔中。 如需詳細資訊，請參閱 <<c0> [ 變更符號標頭檔的名稱](../windows/changing-the-names-of-symbol-header-files.md)。|
|**唯讀符號指示詞**|可讓您包含標頭檔包含不應該修改的編輯工作階段期間的符號。 例如，您可以包含數個專案之間共用的符號檔案。 您也可以包含 MFC.h 檔案。 如需詳細資訊，請參閱 <<c0> [ 包含共用 （唯讀） 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)。|
|**編譯時間指示詞**|可讓您包含會個別建立和編輯從您的主要資源檔中的資源的資源檔包含編譯時間指示詞 （例如這些指示詞有條件地包含資源），或包含自訂格式的資源。 您也可以使用**編譯時間指示詞方塊**包含標準 MFC 資源檔。|

> [!NOTE]
> 這些文字方塊中的項目剢謅.rc 檔餇標示`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分別。 如需詳細資訊，請參閱[TN035:使用 Visual c + + 中的多個資源檔和標頭檔](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

一旦您已使用資源檔案變更**Resource Includes**  對話方塊中，您需要關閉.rc 檔案，然後再重新開啟，讓變更生效。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>在編譯時期，於專案中包含資源

1. 將資源放在包含唯一檔案名稱的資源指令碼檔案。 不用*projectname*.rc，因為此名稱已使用的主要資源指令碼檔案的檔案名稱。

1. 以滑鼠右鍵按一下.rc 檔 (在[資源檢視](../windows/resource-view-window.md))，然後選擇**Resource Includes**從捷徑功能表。

1. 在 **編譯時間指示詞**方塊中，加入[#include](../preprocessor/hash-include-directive-c-cpp.md)編譯器指示詞，以在開發環境中的主要資源檔中納入新的資源檔。

   以這種方式包含的檔案中資源，都會在編譯時期成為可執行檔的一部分。 當您正在處理您的專案主要.rc 檔時，它們無法直接使用編輯或修改。 個別開啟包含的.rc 檔。 任何包含但不含.rc 副檔名的檔案不是可編輯的資源編輯器。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>若要指定特定的資源 （.rc 檔） 的 include 目錄

1. 以滑鼠右鍵按一下方案總管 中的.rc 檔，然後選取**屬性**從捷徑功能表。

1. 選取 **資源**的左窗格中的節點，並指定任何其他 include 目錄中的**其他 include 目錄**屬性。

### <a name="to-find-symbols-in-resources"></a>若要尋找資源中的符號

1. 從**編輯**功能表上，選擇[尋找符號](/visualstudio/ide/go-to)。

1. 在  **Find What**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找的快速鍵 (例如`ID_ACCEL1`)。

   > [!TIP]
   > 若要使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)進行搜尋，您必須使用[檔案中尋找命令](/visualstudio/ide/reference/find-command)從**編輯**功能表，而不是**尋找符號**命令。 若要啟用的規則運算式，您必須擁有**使用：規則運算式**中選取的核取方塊[尋找對話方塊](/visualstudio/ide/finding-and-replacing-text)。 接著，您可以選取右邊的向右箭號按鈕**Find What**方塊，以顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替換成索引中的搜尋文字**Find What**  方塊中。

1. 選取任一**尋找**選項，然後選擇**尋找下一個**。

> [!NOTE]
> 您無法在字串、快速鍵或二進位資源中搜尋符號。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[建立資源](../windows/how-to-create-a-resource-script-file.md)<br/>
[管理資源](../windows/how-to-copy-resources.md)<br/>