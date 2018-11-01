---
title: 建立新的工具列 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
ms.openlocfilehash: 3c36579560c78ff77a624e4827df9d6a9302ae57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551303"
---
# <a name="creating-new-toolbars-c"></a>建立新的工具列 （c + +）

### <a name="to-create-a-new-toolbar"></a>若要建立新的工具列

1. 在  **Resource**檢視，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。 (如果您將現有工具列在.rc 檔時，您可以直接以滑鼠右鍵按一下 **工具列**資料夾，然後選取**插入工具列**從捷徑功能表。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 **加入資源**對話方塊中，選取**工具列**中**資源類型**清單，然後按一下**新增**。

   如果一個加號 (**+**) 旁邊會出現**工具列**資源類型，表示工具列範本可供使用。 按一下加號，展開 範本清單，選取範本，然後按一下**新增**。

   \-或-

3. [將現有點陣圖轉換成工具列](../windows/converting-bitmaps-to-toolbars.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC 或 ATL

## <a name="see-also"></a>另請參閱

[工具列編輯器](../windows/toolbar-editor.md)