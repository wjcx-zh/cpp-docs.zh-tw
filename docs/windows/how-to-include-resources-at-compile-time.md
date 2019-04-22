---
title: HOW TO：在編譯時期包含資源 (C++)
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
ms.openlocfilehash: ca24a10f905e61feb2b090ba3966c752db3d4444
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041496"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>HOW TO：在編譯時期包含資源 (C++)

根據預設，所有的資源位於一個資源指令碼 (.rc) 檔，不過有許多原因會放置在主要.rc 檔以外的檔案中的資源：

- 若要儲存.rc 檔時不會刪除的資源陳述式中加入註解。

- 若要包含已完成開發及測試的資源，而且不需要進一步修改。 任何包含但不含.rc 副檔名的檔案不是可編輯的資源編輯器。

- 若要包含的資源正在使用不同的專案，或屬於原始程式碼版本控制系統。 這些資源必須存在於修改將會影響所有專案的中央位置。

- 若要包含資源 （例如 RCDATA 資源） 的自訂格式。 RCDATA 資源有您不能在其中使用的值為運算式的特殊需求`nameID`欄位。

如果您將區段在現有的.rc 檔符合下列任一條件時，將這些區段放在一個或多個個別.rc 檔，並將它們包含在專案中使用**Resource Includes**  對話方塊。

## <a name="resource-includes"></a>資源包含

您可以將資源從其他檔案加入您的專案在編譯時期藉由列出在**編譯時間指示詞**方塊中**Resource Includes**  對話方塊。 使用**Resource Includes**對話方塊來修改專案.rc 檔，以及所有儲存的所有資源的專案環境的一般工作安排[符號](../windows/symbols-resource-identifiers.md)在`Resource.h`。

若要開始，開啟**Resource Includes**對話方塊中，以滑鼠右鍵按一下.rc 檔中的[資源檢視](how-to-create-a-resource-script-file.md#create-resources)，選取**Resource Includes**並記下下列屬性：

| 屬性 | 描述 |
|---|---|
| **符號標頭檔** | 可讓您變更儲存您的資源檔的符號定義的標頭檔的名稱。<br/><br/>如需詳細資訊，請參閱 <<c0> [ 變更符號標頭檔的名稱](../windows/changing-the-names-of-symbol-header-files.md)。 |
| **唯讀符號指示詞** | 可讓您包含標頭檔包含不應該修改的符號。<br/><br/>比方說，符號檔案與其他專案共用。 這也可以包含 mfc.h 檔案。 如需詳細資訊，請參閱 <<c0> [ 包含共用 （唯讀） 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)。 |
| **編譯時間指示詞** | 可讓您包含會個別建立和編輯從您的主要資源檔中的資源的資源檔包含編譯時間指示詞 （例如這些指示詞有條件地包含資源），或包含自訂格式的資源。<br/><br/>您也可以使用**編譯時間指示詞方塊**包含標準 MFC 資源檔。 |

> [!NOTE]
> 這些文字方塊中的項目剢謅.rc 檔餇標示`TEXTINCLUDE 1`， `TEXTINCLUDE 2`，和`TEXTINCLUDE 3`分別。 如需詳細資訊，請參閱[TN035:使用視覺效果中的多個資源檔和標頭檔C++ ](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

使用資源檔案進行變更之後**Resource Includes**  對話方塊中，您必須關閉再重新開啟 *.rc*檔案，變更才會生效。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>在編譯時期，於專案中包含資源

1. 將資源放在包含唯一檔案名稱的資源指令碼檔案。 不用*projectname.rc*，因為這是用於主要資源指令碼檔案的檔案名稱。

1. 以滑鼠右鍵按一下 *.rc*中的檔案[資源檢視](how-to-create-a-resource-script-file.md#create-resources)，然後選取**Resource Includes**。

1. 在 **編譯時間指示詞**方塊中，加入[#include](../preprocessor/hash-include-directive-c-cpp.md)編譯器指示詞，以在開發環境中的主要資源檔中納入新的資源檔。

包含這種方式的檔案中的資源在編譯時期皆可執行檔的一部分，並不適用於編輯或修改時您正在處理您的專案主要.rc 檔。 包含的.rc 檔需要個別開啟，而且任何包含不含.rc 副檔名的檔案不是可編輯的資源編輯器。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>若要指定特定資源 (.rc) 檔的 include 目錄

1. 以滑鼠右鍵按一下 *.rc*中的檔案**方案總管**，然後選取**屬性**。

1. 選取 **資源**的左窗格中的節點，並指定任何其他 include 目錄中的**其他 include 目錄**屬性。

### <a name="to-find-symbols-in-resources"></a>若要尋找資源中的符號

1. 移至功能表**編輯** > [尋找符號](/visualstudio/ide/go-to)。

   > [!TIP]
   > 若要使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)在搜尋中，選取[檔案中尋找](/visualstudio/ide/reference/find-command)中**編輯**功能表，而不是**尋找符號**。 選取**使用：規則運算式**中的核取方塊[尋找對話方塊](/visualstudio/ide/finding-and-replacing-text)然後在**尋找目標**方塊，您可以從下拉式清單中選擇規則搜尋運算式。 當您從這份清單中選取運算式時，它會替換成索引中的搜尋文字**Find What**  方塊中。

1. 在  **Find What**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找此項目，例如的快速鍵`ID_ACCEL1`。

1. 選取任一**尋找**選項，然後選擇**尋找下一個**。

> [!NOTE]
> 您無法在字串、快速鍵或二進位資源中搜尋符號。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：建立資源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：管理來源](../windows/how-to-copy-resources.md)<br/>