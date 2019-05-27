---
title: 作法：將自訂工具整合至專案屬性中
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837036"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>作法：將自訂工具整合至專案屬性中

您可以建立基礎 XML 結構描述檔案，以將自訂工具選項新增至 Visual Studio 的 [屬性頁] 視窗。

[屬性頁] 視窗的 [組態屬性] 區段會顯示設定群組，也就是*規則*。 每個規則都包含一項工具或一組功能的設定。 例如，**連結器**規則包含連結器工具的設定。 規則中的設定可以細分為*分類*。

本文件說明如何在已設定的目錄中建立檔案，其中包含可讓屬性在 Visual Studio 啟動時載入的自訂工具屬性。 如需如何修改檔案的詳細資訊，請參閱 Visual Studio 專案團隊部落格上的[平台延展性第 2 部分](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/)。

### <a name="to-add-or-change-project-properties"></a>新增或變更專案屬性

1. 在 XML 編輯器中，建立 XML 檔案。

1. 將檔案儲存在 Visual Studio `VCTargets\1033` 資料夾中。 您安裝的每個 Visual Studio 版本和每個語言分別會有不同的路徑。 例如，英文版的 Visual Studio 2019 Community 的預設資料夾路徑為 `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`。 調整您的語言和 Visual Studio 版本的路徑。 [屬性頁] 視窗中的每個規則都會以此資料夾中的 XML 檔案表示。 請確定該檔案的名稱在此資料夾中是唯一的。

1. 複製 `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` 的內容 (或您的路徑)，並加以關閉而不儲存變更，然後將內容貼到新的 XML 檔案中。 您可以使用任何 XML 結構描述檔案 - 這只是可讓您開始使用範本的檔案。

1. 在新的 XML 檔案中，根據您的需求修改內容。 請務必在檔案頂端變更**規則名稱**和 **Rule.DisplayName**。

1. 儲存變更並關閉檔案。

1. `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (或您儲存這些檔案的位置) 中的 XML 檔案會在 Visual Studio 啟動時載入。 因此，若要測試新的檔案，請重新啟動 Visual Studio。

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]。 在 [屬性頁] 視窗的左窗格中確認有新的節點，且該節點具有您的規則名稱。

## <a name="see-also"></a>另請參閱

[命令列上的 MSBuild - C++](msbuild-visual-cpp.md)
