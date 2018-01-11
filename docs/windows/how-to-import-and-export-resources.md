---
title: "如何： 匯入和匯出資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a01269928d0e5b52cca6e2301ad681db61289f80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-import-and-export-resources"></a>如何：匯入和匯出資源
您可以匯入圖形資源 (點陣圖、圖示、游標和工具列)、HTML 檔案，及在 Visual C++ 中使用的自訂資源。 您可以從 Visual C++ 專案匯出相同類型的檔案，分隔可以在開發環境外部使用的檔案。  
  
> [!NOTE]
>  資源類型 (例如加速器、對話方塊和字串資料表) 無法匯入或匯出，因為它們不是獨立的檔案類型。  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>將個別的資源匯入目前的資源檔  
  
1.  在[資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下節點的資源指令碼 (*.rc) 您要將資源加入的檔案。  
  
2.  按一下**匯入**快顯功能表。  
  
3.  找出並選取點陣圖 (.bmp)、圖示 (.ico)、游標 (.cur)、Html 檔案 (.htm)，或是您要匯入的其他檔案的檔案名稱。  
  
4.  按一下**確定**，將資源加入至選取的檔案中**資源**檢視。  
  
    > [!NOTE]
    >  無論選取哪一種特定的資源類型，匯入程序都會以相同的方式運作。 會針對該資源類型，將匯入的資源自動加入至正確的節點。  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>匯出點陣圖、圖示或游標做為個別的檔案 (在 Visual C++ 外部使用)  
  
1.  在**資源**檢視中，以滑鼠右鍵按一下您想要匯出的資源。  
  
2.  按一下**匯出**快顯功能表。  
  
3.  在**匯出資源**對話方塊方塊中，接受目前的檔案名稱或輸入新。  
  
4.  瀏覽至您要儲存檔案，然後按一下資料夾**匯出**。  
  

  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)