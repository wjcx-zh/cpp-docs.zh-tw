---
title: 如何： 使用資源範本 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- language-specific template files [C++]
- resource templates
- resources [C++], creating
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90c94e87693929c2ae33d65fe3f3a4b2dd55d48b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313971"
---
# <a name="how-to-use-resource-templates-c"></a>如何： 使用資源範本 （c + +）

資源範本是您已儲存為 .rct 檔案的自訂資源。 資源範本之後可以做為建立其他資源的起點。 資源範本可節省在開發共用功能的其他資源或資源群組的時間，例如標準控制項和其他重複的項目。 例如，您可能想要在數個對話方塊中包含 [說明] 按鈕和公司標誌的圖示。 若要快速地執行，請建立新對話方塊範本並使用標誌與 [說明] 按鈕加以自訂。

一旦您已自訂資源範本，您必須在範本資料夾 （或指定 include 路徑中的任何位置） 中儲存變更，讓新的資源範本會出現在其資源類型底下[加入資源對話方塊](../windows/add-resource-dialog-box.md). 然後您可以視需要經常使用新資源範本。

> [!NOTE]
> 您可以將特定語言的範本檔置於主要範本目錄的子目錄中。 比方說，您可以將僅限英文版的範本檔案中放\\< 資源範本目錄\>\1033。

### <a name="to-create-a-template-for-resources"></a>建立資源的範本

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下您的專案。

2. 從捷徑功能表，選擇**新增**，然後按一下**加入新項目**。

3. 在 **加入新項目**對話方塊中，於**範本：** 窗格中，選擇**資源範本檔 (.rct)**。

4. 提供的名稱和您的新.rct 檔案的位置，然後按**開啟**。

5. 新的.rct 檔案新增至您的專案，並出現在**方案總管**下方**資源**資料夾。

   您現在可以按兩下.rct 檔案以在文件視窗中，開啟它，然後將資源新增至它 (以滑鼠右鍵按一下 文件視窗中的檔案，然後選擇 **加入資源**從快顯功能表)。 然後，您可以自訂這些資源，並儲存 .rct 檔案。

   > [!NOTE]
   > 當您建立新 RCT 檔案時，Visual Studio 就會在搜尋 \Program Files\Microsoft Visual Studio 9.0\vc\vcresourcetemplates、\program \Program Files\Microsoft Visual Studio 9.0\vc\vcresourcetemplates、\program\\*LCID* (例如 1033 代表英文)*或是*上的任何位置[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 如果您偏好要將 RCT 檔案儲存在另一個檔案資料夾，例如 \我的文件，您只需要將此資料夾加入至 include 路徑，Visual Studio 將會找到您的 RCT 檔案。

### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>將現有的 .rc 檔轉換成 .rct 檔案

1. [將.rc 檔案開啟為獨立檔案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

2. 在 **檔案**功能表上，按一下**儲存\<*您的檔案名稱*> 做為**。

3. 指定的位置，然後按一下**確定**。

### <a name="to-create-a-new-resource-from-a-template"></a>從範本建立新資源

1. 在 [資源檢視](../windows/resource-view-window.md)窗格中，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。

2. 在 **加入資源**對話方塊方塊中，按一下加號 (**+**) 旁的展開 資源 節點，並查看該資源可用的所有範本的資源。

3. 按兩下您想要使用的範本。

4. 在資源編輯器中視需要修改所加入的資源。

   資源編輯器會自動提供唯一的資源識別碼。 您可以修改[資源內容](../windows/changing-the-properties-of-a-resource.md)視。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)  
[資源編輯器](../windows/resource-editors.md)