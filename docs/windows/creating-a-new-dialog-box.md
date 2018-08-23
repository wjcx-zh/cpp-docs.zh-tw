---
title: 建立新的對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, creating
- Dialog editor, creating dialog boxes
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8cd214cdf2a3d4677464c98ca1c950a5c1891a42
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584152"
---
# <a name="creating-a-new-dialog-box"></a>建立新的對話方塊

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

[如何：建立資源](../windows/how-to-create-a-resource.md)  
[資源檔](../windows/resource-files-visual-studio.md)  
[對話方塊編輯器](../windows/dialog-editor.md)