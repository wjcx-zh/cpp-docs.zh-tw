---
title: HOW TO：建立資源指令碼檔案 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: f3f0adff256742c98a672e40e6b31de9bd7a84ed
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849954"
---
# <a name="how-to-create-a-resource-script-file-c"></a>HOW TO：建立資源指令碼檔案 （c + +）

> [!NOTE]
> **資源編輯器**不適用於 Express 版本。
>
> 這份資料適用於 Windows 桌面應用程式。 以 .NET 語言撰寫的專案不會使用資源指令碼檔。 如需詳細資訊，請參閱 <<c0> [ 資源檔](../windows/resource-files-visual-studio.md)，如需詳細資訊。

## <a name="to-create-a-new-resource-script-rc-file"></a>建立新的資源指令碼 (.rc) 檔

1. 將焦點放在您現有的專案資料夾中**方案總管**，例如`MyProject`。

   > [!NOTE]
   > 請勿混淆方案資料夾內專案資料夾**方案總管 中**。 如果您將焦點放在**解決方案**資料夾中，您的選擇中**加入新項目**對話方塊 （在步驟 3) 將會不同。

1. 在 [專案] 功能表中，選取 [新增新項目]。

1. 在 **加入新項目**對話方塊中，選取**Visual c + +** 資料夾，然後選擇**資源檔 (.rc)** 右窗格中。

1. 提供資源指令碼檔案中的名稱**名稱**文字，然後選擇**開啟**。

您現在可以 [建立](../windows/how-to-create-a-resource.md) 新的資源並加入 .rc 檔中。

> [!NOTE]
> 您只能將資源指令碼 (.rc 檔) 加入已載入 Visual Studio IDE 的現有專案中， 而不能建立獨立的 .rc 檔 (即專案以外的檔案)。 [資源範本](../windows/how-to-use-resource-templates.md) (.rct 檔) 則可以隨時建立。

## <a name="to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>若要開啟 c + + 專案 （獨立式） 外的資源指令碼檔案

您可以檢視 .rc 檔中的資源，而不需要開啟一個專案。 .Rc 檔會在相對於在文件視窗中開啟[資源檢視](../windows/resource-view-window.md)視窗 （如同在專案內開啟檔案時）。

> [!NOTE]
> 這是一項重要的差異，因為某些命令只有在獨立開啟檔案時 (在專案外)，才可供使用。 比方說，您可以只將檔案儲存在不同的格式或不同的檔案名稱在專案外開啟檔案時 (**另存新檔**專案內開啟的檔案時，命令便無法使用)。

### <a name="to-open-an-rc-file-outside-a-project"></a>開啟專案外部的 .rc 檔案

1. 從**檔案**功能表上，選擇**開放**，然後選取**檔案**。

1. 在 **開啟的檔案**對話方塊方塊中，瀏覽至您想要檢視、 反白顯示檔案，然後選取資源指令碼檔**開啟**。

   > [!NOTE]
   > 如果您第一次開啟專案 (**檔案**，**開啟**，**專案**)，有些命令不會提供給您。 「獨立」開啟檔案表示開啟檔案而不先載入專案。

### <a name="to-open-multiple-rc-files-outside-a-project"></a>開啟專案外的多個 .rc 檔

1. 開啟兩個獨立資源檔案。 例如，開啟`Source1.rc`和`Source2.rc`。

   1. 從**檔案**功能表上，選擇**開放**，然後選取**檔案**。

   1. 在 **開啟的檔案**對話方塊方塊中，巡覽至您想要開啟的第一個資源指令碼檔案 (`Source1.rc`)，反白顯示檔案，然後選擇**開啟**。

   1. 重複上述步驟來開啟第二個.rc 檔餇 (`Source2.rc`)。

       .rc 檔現在會在個別的文件視窗中開啟。

1. 開啟兩個 .rc 檔時，並排顯示視窗，以讓您同時檢視：

   - 從** 視窗**功能表上，選擇**新增水平索引標籤群組**或是**新增垂直索引標籤群組**。

       \-或-

   - 以滑鼠右鍵按一下其中一個.rc 檔，然後選擇 **新增的水平索引標籤群組**或是**新增垂直索引標籤群組**從捷徑功能表。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

## <a name="to-open-a-resource-script-file-in-text-format"></a>若要以文字格式開啟資源指令碼檔

有時候您會想要檢視專案資源指令碼 (.rc) 檔內容，而不想開啟其特定資源編輯器內的資源 (例如對話方塊)。 例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。

> [!NOTE]
> 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

您可以輕鬆開啟資源檔，以文字格式，檢視它所包含的所有資源，並完成文字編輯器所支援的通用作業。

> [!NOTE]
> 資源編輯器不會直接讀取.rc 或`resource.h`檔案。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 (例如註解)。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。

### <a name="to-open-a-resource-script-file-as-text"></a>將資源指令碼檔開啟為文字

1. 從**檔案**功能表中選擇 **開放**，然後選擇**檔案**。

1. 在 **開啟檔案**對話方塊方塊中，瀏覽至您想要以文字格式檢視資源指令碼檔。

1. 反白顯示檔案，然後選取上的下拉箭號**開啟**按鈕 （位於按鈕右邊）。

1. 選擇**開啟**從下拉式選單。

1. 在 **開啟**對話方塊中，選取**原始程式碼 （文字） 編輯器**。

1. 從**開啟為**下拉式清單中，選取**文字**。

   資源會在中開啟**原始程式碼**編輯器。

\-或-

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下.rc 檔。

1. 從捷徑功能表，選擇 **開啟方式...**，然後選取**原始程式碼 （文字） 編輯器**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)<br/>
[資源編輯器](../windows/resource-editors.md)