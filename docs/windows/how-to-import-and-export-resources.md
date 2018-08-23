---
title: 如何： 匯入和匯出資源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d6e2c3a27204ffb6e1c23f158f1f3fdc93a792e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596967"
---
# <a name="how-to-import-and-export-resources"></a>如何：匯入和匯出資源

您可以匯入圖形資源 (點陣圖、圖示、游標和工具列)、HTML 檔案，及在 Visual C++ 中使用的自訂資源。 您可以從 Visual C++ 專案匯出相同類型的檔案，分隔可以在開發環境外部使用的檔案。

> [!NOTE]
> 資源類型 (例如加速器、對話方塊和字串資料表) 無法匯入或匯出，因為它們不是獨立的檔案類型。

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>將個別的資源匯入目前的資源檔

1. 在[資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下 [] 節點的資源指令碼 (*.rc) 您要將資源新增的檔案。

2. 按一下 **匯入**快顯功能表。

3. 找出並選取點陣圖 (.bmp)、圖示 (.ico)、游標 (.cur)、Html 檔案 (.htm)，或是您要匯入的其他檔案的檔案名稱。

4. 按一下  **確定**中選取的檔案中加入資源**資源**檢視。

   > [!NOTE]
   > 無論選取哪一種特定的資源類型，匯入程序都會以相同的方式運作。 會針對該資源類型，將匯入的資源自動加入至正確的節點。

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>匯出點陣圖、圖示或游標做為個別的檔案 (在 Visual C++ 外部使用)

1. 在 **資源**檢視中，以滑鼠右鍵按一下您想要匯出的資源。

2. 按一下 **匯出**快顯功能表。

3. 在 **匯出資源**對話方塊方塊中，接受目前的檔案名稱或輸入新密碼。

4. 瀏覽至您想要用來儲存檔案，然後按一下 資料夾**匯出**。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)  
[資源編輯器](../windows/resource-editors.md)