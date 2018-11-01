---
title: 建立新的對話方塊 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: ed1bb21029b2a61eb51b54386ed51ef08b90e149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605312"
---
# <a name="creating-a-new-dialog-box-c"></a>建立新的對話方塊 （c + +）

### <a name="to-create-a-new-dialog-box"></a>若要建立新的對話方塊

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 **加入資源**對話方塊中，選取**對話方塊**中**資源類型**清單，然後按一下**新增**。

   如果一個加號 (**+**) 旁邊會出現**對話方塊**資源類型，表示對話方塊範本都可用。 按一下加號，展開 範本清單，選取範本，然後按一下**新增**。

   在中，開啟 [新增] 對話方塊 **對話方塊**編輯器。

   您也可以[ 對話方塊編輯器中開啟現有的對話方塊，編輯](../windows/viewing-and-editing-resources-in-a-resource-editor.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[如何：建立資源](../windows/how-to-create-a-resource.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)