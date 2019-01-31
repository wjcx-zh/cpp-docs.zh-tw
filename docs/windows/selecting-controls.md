---
title: 選取控制項
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.author: Michael.Blome
ms.topic: tutorial
ms.service: cpp
author: mikeblome
ms.openlocfilehash: 008c99ae4b2cba5ff8f8b9ab069bb1b8085b7524
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293633"
---
# <a name="selecting-controls"></a>選取控制項

選取控制項來調整大小、 對齊、 移動、 複製或刪除它們，然後完成您要的作業。 在大部分情況下，您必須選取要使用的調整大小和對齊工具上的多個控制項[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

當控制項被選取時，它具有實線 (active）) 其周圍的灰色的框線或中空 （非作用中） 「 調整大小控點，「 小方塊，會出現在選取範圍框線。 選取多個控制項時，主控制項有穩固的調整大小控點，而且所有其他選取的控制項有空心的調整大小控點。

當您調整大小或對齊多個控制項， ** 對話方塊**編輯器會使用 「 主控制項 」 來判斷如何調整大小或對齊其他控制項。 根據預設，主控制項是第一個選取的控制項。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="to-select-multiple-controls"></a>若要選取多個控制項

1. 在  [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)，選取**指標**工具。

1. 拖曳指標以繪製您想要在您的對話方塊中選取的控制項周圍的選取方塊。

   當您放開滑鼠按鈕時，所有控制項內、 交集與選取方塊已選取。

   \-或-

   按住**Shift**鍵並選取您想要在選取項目中包含的控制項。

   \-或-

   按住**Ctrl**鍵並選取您想要在選取項目中包含的控制項。

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>若要移除的一組選取的控制項的控制項，或將控制項新增至選取的控制項的群組

1. 使用選取的控制項群組，請按住**Shift**鍵並選取您想要移除或加入到現有的選取範圍的控制項。

   > [!NOTE]
   > 按住**Ctrl**索引鍵，然後選取 選取範圍內的控制項將此控制項主控該選取項目中。

## <a name="to-specify-the-dominant-control"></a>若要指定主控項

1. 按住**Ctrl**鍵，然後按一下您想要的大小或其他控制項的位置會影響的控制項*第一個*。

> [!NOTE]
> 空心下層控制項的控制代碼時，主控項的調整大小控點是純色。 所有進一步調整大小或對齊根據主控制項。

## <a name="to-change-the-dominant-control"></a>若要變更主控項

1. 所有目前選取的控制項外按一下，以清除目前的選取範圍。

1. 重複上一個程序，第一次選取不同的控制項。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)