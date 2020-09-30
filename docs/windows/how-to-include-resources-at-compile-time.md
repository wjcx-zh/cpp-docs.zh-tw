---
title: '如何：在編譯時期包含資源 (c + +) '
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
ms.openlocfilehash: 5ac4cba4e8ad8a08fa1010758c5a343501d3af2c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504408"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>如何：在編譯時期包含資源 (c + +) 

根據預設，所有資源都位於一個資源腳本 ( .rc) 檔案中，不過有許多原因會將資源放在主要 .rc 檔以外的檔案中：

- 將批註新增至當您儲存 .rc 檔時不會被刪除的資源語句。

- 包含已經開發和測試但不需要進一步修改的資源。 資源編輯器將無法編輯任何包含但不具有 .rc 副檔名的檔案。

- 包含不同專案所使用的資源，或屬於原始程式碼版本控制系統一部分的資源。 這些資源必須存在於修改會影響所有專案的中央位置。

- 包含資源 (例如自訂格式) 的 RCDATA 資源。 RCDATA 資源具有特殊需求，您無法使用運算式作為欄位的值 `nameID` 。

如果您現有的 .rc 檔中有一些區段符合上述任何條件，請將這些區段放在一或多個個別的 .rc 檔案中，並使用 [ **資源包含** ] 對話方塊將這些區段包含在專案中。

## <a name="resource-includes"></a>資源包含

您可以在編譯時期將其他檔案中的資源新增至專案，方法是在 [**資源包含**] 對話方塊的 [**編譯時間**指示詞] 方塊中列出它們。 您可以使用 [ **資源包含** ] 對話方塊來修改專案環境中，將所有資源儲存在專案 .rc 檔中的正常運作方式，以及中的所有 [符號](../windows/symbols-resource-identifiers.md) `Resource.h` 。

若要開始使用，請開啟 [ **資源包含** ] 對話方塊，方法是以滑鼠右鍵按一下 [資源檢視](how-to-create-a-resource-script-file.md#create-resources)中的 .rc 檔，選取 [ **資源包含** ]，並記下下列屬性：

| 屬性 | 描述 |
|---|---|
| **符號標頭檔** | 可讓您變更儲存資源檔符號定義的標頭檔名稱。<br/><br/>如需詳細資訊，請參閱 [變更符號標頭檔的名稱](./changing-a-symbol-or-symbol-name-id.md)。 |
| **唯讀符號指示詞** | 可讓您包含不應該修改之符號的標頭檔。<br/><br/>例如，要與其他專案共用的符號檔。 這也可以包含 MFC .h 檔案。 如需詳細資訊，請參閱 [包含共用 (唯讀) 或計算符號](./changing-a-symbol-or-symbol-name-id.md)。 |
| **編譯時間指示詞** | 可讓您包含與主要資源檔中的資源分開建立和編輯的資源檔，其中包含編譯時間指示詞 (例如，有條件地包含資源) 的指示詞，或包含自訂格式的資源。<br/><br/>您也可以使用 [ **編譯時間** 指示詞] 方塊來包含標準 MFC 資源檔。 |

> [!NOTE]
> 這些文字方塊中的專案會出現在分別以、和標記的 .rc 檔中 `TEXTINCLUDE 1` `TEXTINCLUDE 2` `TEXTINCLUDE 3` 。 如需詳細資訊，請參閱 [TN035：搭配 Visual C++ 使用多個資源檔和標頭檔](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。

使用 [ **資源包含** ] 對話方塊變更資源檔之後，您必須關閉並重新開啟 *.rc* 檔，變更才會生效。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>在編譯時期，於專案中包含資源

1. 將資源放在包含唯一檔案名稱的資源指令碼檔案。 請勿使用 *專案*名稱，因為這是主要資源腳本檔案所用的檔案名。

1. 在[資源檢視](how-to-create-a-resource-script-file.md#create-resources)中，以滑鼠右鍵按一下 *.rc*檔，然後選取 [**資源包含**]。

1. 在 [ **編譯時間** 指示詞] 方塊中，加入 [#include](../preprocessor/hash-include-directive-c-cpp.md) 編譯器指示詞，在開發環境中的主要資源檔內包含新的資源檔。

以這種方式包含的檔案中的資源，只會在編譯時期成為可執行檔的一部分，而且當您處理專案的主要 .rc 檔時，無法進行編輯或修改。 包含的 .rc 檔必須分開開啟，而且資源編輯器不會編輯包含 .rc 副檔名的任何檔案。

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>若要指定特定資源的 include 目錄 ( .rc) 檔

1. 在**方案總管**中，以滑鼠右鍵按一下 *.rc*檔，然後選取 [**屬性**]。

1. 選取左窗格中的 [ **資源** ] 節點，然後在 [ **其他 include 目錄** ] 屬性中指定任何其他的 include 目錄。

### <a name="to-find-symbols-in-resources"></a>若要尋找資源中的符號

1. 移至功能表**編輯**  >  [尋找符號](/visualstudio/ide/go-to)。

   > [!TIP]
   > 若要在搜尋中使用[正則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)，請選取 [**編輯**] 功能表中的 [在檔案中[尋找](/visualstudio/ide/reference/find-command)]，而不是**尋找符號**。 在 [[尋找] 對話方塊](/visualstudio/ide/finding-and-replacing-text)中選取 [**使用：正則運算式**] 核取方塊，然後在 [**尋找目標**] 方塊中，從下拉式清單中選擇一般搜尋運算式。 當您從這份清單中選取運算式時，它會取代為 [ **尋找目標** ] 方塊中的搜尋文字。

1. 在 [ **尋找目標** ] 方塊中，從下拉式清單中選取先前的搜尋字串，或輸入您想要尋找的快速鍵，例如 `ID_ACCEL1` 。

1. 選取任何 [ **尋找** ] 選項，然後選擇 [ **尋找下一個]**。

> [!NOTE]
> 您無法在字串、快速鍵或二進位資源中搜尋符號。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[如何：建立資源](../windows/how-to-create-a-resource-script-file.md)<br/>
[如何：管理資源](../windows/how-to-copy-resources.md)<br/>
