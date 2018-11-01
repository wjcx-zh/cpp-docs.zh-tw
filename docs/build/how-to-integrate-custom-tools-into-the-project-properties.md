---
title: 如何：將自訂工具整合至專案屬性中
ms.date: 04/27/2016
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 7041e6583ba1e2c7f035edcc72617ccdb8d5aa02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633008"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>如何：將自訂工具整合至專案屬性中

您可以加入 Visual Studio 中的自訂工具選項**屬性頁**視窗建立基礎 XML 結構描述檔案。

**組態屬性**一節**屬性頁** 視窗會顯示設定群組，也就*規則*。 每個規則都包含一項工具或一組功能的設定。 例如，**連結器**規則包含連結器工具的設定。 在規則中的設定可以細分*分類*。

本文件說明如何建立包含您的自訂工具的屬性，讓 Visual Studio 啟動時，會載入屬性的設定目錄中的檔案。 如需有關如何修改檔案的資訊，請參閱 <<c0> [ 平台延展性第 2 部分](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/)Visual Studio 專案團隊部落格上。

### <a name="to-add-or-change-project-properties"></a>若要新增或變更專案屬性

1. 在 XML 編輯器中，建立 XML 檔案。

1. 將檔案儲存在 Visual Studio 2017`VCTargets\1033`資料夾。 您必須已安裝的 Visual Studio 2017 的每個版本和每個語言的不同路徑。 例如，英文版的 Visual Studio Enterprise 版本的資料夾路徑是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 調整您的語言和 Visual Studio 版本的路徑。 在每個規則**屬性頁**視窗由這個資料夾中的 XML 檔案。 請確定檔案唯一名稱的資料夾中。

1. 將內容複製`%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`，關閉但不儲存變更，然後將內容貼到新的 XML 檔案。 您可以使用任何 XML 結構描述檔案-這只是其中一個可讓您開始使用範本。

1. 在新的 XML 檔案中，修改的內容，根據您的需求。 請務必變更**Rule Name**並**Rule.DisplayName**在檔案頂端。

1. 儲存變更並關閉檔案。

1. 中的 XML 檔案`%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>`Visual Studio 啟動時載入。 因此，若要測試新的檔案，請重新啟動 Visual Studio。

1. 在 **方案總管**，以滑鼠右鍵按一下專案，然後按一下**屬性**。 在 **屬性頁**視窗中的，在左窗格中，確認有新的節點，以您的規則的名稱。

## <a name="see-also"></a>另請參閱

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
