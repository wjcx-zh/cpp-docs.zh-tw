---
title: 編輯影像 （圖示影像編輯器） 的部分 |Microsoft 文件
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
ms.openlocfilehash: b33a591a2f38062b5eaf81b0f56ab73a36f4c90c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>編輯影像部分範圍 (圖示影像編輯器)
您可以執行標準的編輯作業： 剪下、 複製、 清除和移動 — 上[選取](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)、 選取範圍是整個映像或只是它的一部分。 由於影像編輯器會使用 Windows 剪貼簿，您可以在影像編輯器和其他 Windows 應用程式之間傳輸映像。  
  
 此外，您可以調整選取項目，是否包含整個影像或組件。  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>剪下目前的選取範圍，並將它移到剪貼簿  
  
1.  按一下**剪下**上**編輯**功能表。  
  
### <a name="to-copy-the-selection"></a>複製選取項目  
  
1.  內部選取框線或任何位置將指標放在其上，調整大小控點除外。  
  
2.  按住**CTRL**鍵您將選取項目拖曳至新位置。 原始選取項目的區域保持不變。  
  
3.  若要複製其目前位置的映像選取項目，按一下選取範圍的資料指標外部。  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>若要將剪貼簿內容貼到影像  
  
1.  從**編輯**功能表上，選擇**貼上**。  
  
     剪貼簿的內容，以選取項目框線括住會出現在窗格的左上角。  
  
2.  選取框線中的將指標放在與映像上，將影像拖曳至想要的位置。  
  
3.  若要錨定在其新位置的映像，按一下 外部選取框線。  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>若要刪除目前選取範圍，而不將它移到剪貼簿  
  
1.  從**編輯**功能表上，選擇**刪除**。  
  
     選取項目的原始的區域填滿目前的背景色彩。  
  
    > [!NOTE]
    >  您可以存取 剪下、 複製、 貼上，並刪除命令，以滑鼠右鍵按一下 資源檢視 視窗中。  
  
### <a name="to-move-the-selection"></a>移動選取範圍  
  
1.  內部選取框線或任何位置將指標放在其上，調整大小控點除外。  
  
2.  將選取項目拖曳至其新位置。  
  
3.  若要錨定在其新位置的映像選取項目，按一下選取範圍框線外。  
  
 如需有關繪製選取範圍的詳細資訊，請參閱[建立自訂筆刷](../windows/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 無  
  
## <a name="see-also"></a>另請參閱  
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [圖示影像編輯器](../windows/image-editor-for-icons.md)

