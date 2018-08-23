---
title: 編輯組件的影像 （圖示影像編輯器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0380fd6fc9b37c4d7458453398cfbd2ce6699234
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607829"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>編輯影像部分範圍 (圖示影像編輯器)

您可以執行標準的編輯作業： 剪下、 複製、 清除和移動 — 上[選取項目](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)，不論選取範圍是整個影像或加入其中。 因為**映像**編輯器會使用**Windows 剪貼簿**，您可以在傳輸之間的映像**映像**編輯器和其他 Windows 應用程式。

此外，您可以調整大小選項，是否包含整個映像或只是其中一部分。

### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>剪下目前的選取範圍，並將它移到剪貼簿

1. 按一下 **剪下**上**編輯**功能表。

### <a name="to-copy-the-selection"></a>若要複製的選取項目

1. 選取框線內或的任何位置將指標放在其上，除了調整大小控點。

2. 按住**Ctrl**金鑰，您將選取項目拖曳至新位置。 原始的選取範圍的區域不會變更。

3. 將選取範圍複製到映像，在其目前的位置，按一下 選擇資料指標之外。

### <a name="to-paste-the-clipboard-contents-into-an-image"></a>若要將剪貼簿內容貼到映像

1. 從**編輯**功能表上，選擇**貼上**。

   剪貼簿內容，括住選取範圍框線中，會出現在窗格的左上角。

2. 選取框線內將指標放在與映像上，將影像拖曳到想要的位置。

3. 若要錨定在其新位置的映像，請按一下選取範圍框線外。

### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>若要刪除目前選取範圍，而不將它移到剪貼簿

1. 從**編輯**功能表上，選擇**刪除**。

   目前的背景色彩填滿選取範圍的原始區域。

   > [!NOTE]
   > 您可以存取**剪下**，**複製**，**貼上**，以及**刪除**命令，以滑鼠右鍵按一下**資源檢視**  視窗。

### <a name="to-move-the-selection"></a>移動選取範圍

1. 選取框線內或的任何位置將指標放在其上，除了調整大小控點。

2. 將選取項目拖曳至其新位置。

3. 若要錨定在其新位置的映像中的選取範圍，請按一下選取範圍框線外。

如需有關繪製選取範圍的詳細資訊，請參閱[建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)  
[編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[圖示影像編輯器](../windows/image-editor-for-icons.md)