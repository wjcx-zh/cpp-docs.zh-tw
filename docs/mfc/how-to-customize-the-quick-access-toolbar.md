---
title: "如何： 自訂快速存取工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f67d46640a1a4fadc6750ca34b05910902679440
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>如何：自訂快速存取工具列
快速存取工具列 (QAT) 是包含一組命令的可自訂工具列，命令是顯示在 [應用程式] 按鈕旁或類別索引標籤下。 下圖將顯示一般的快速存取工具列。  
  
 ![MFC 功能區快速存取工具列](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")  
  
 若要自訂快速存取工具列，請開啟該**屬性**視窗中，修改其命令，然後再預覽功能區控制項。  
  
### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>在屬性視窗中開啟快速存取工具列  
  
1.  在 Visual Studio 中，在**檢視**功能表上，按一下 **資源檢視**。  
  
2.  在**資源檢視**，按兩下功能區資源以顯示在設計介面上。  
  
3.  設計介面上，快速存取工具列 功能表上按一下滑鼠右鍵，然後按一下 **屬性**。  
  
## <a name="quick-access-toolbar-properties"></a>快速存取工具列屬性  
 下表定義快速存取工具列的屬性。  
  
|屬性|定義|  
|--------------|----------------|  
|QAT 位置|當應用程式啟動時，指定快速存取工具列的位置。 位置可以是**上方**或**下方**功能區控制項。|  
|QAT 項目|指定快速存取工具列可用的命令。|  
  
#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>在快速存取工具列上新增或移除命令  
  
1.  在**屬性**視窗中，按一下  **QAT 項目**，然後按一下省略符號按鈕**（...）**.  
  
2.  在**QAT 項目編輯器**對話方塊中，使用**新增**和**移除**按鈕，以修改快速存取工具列上的命令清單。  
  
3.  如果您想要命令顯示在快速存取工具列和快速存取工具列功能表上，請選取命令旁的方塊。 如果您想要命令只出現在功能表中，請清除方塊。  
  
## <a name="previewing-the-ribbon"></a>預覽功能區  
 快速存取工具列命令未出現在設計介面上。 若要檢視它們，您必須預覽功能區或執行應用程式。  
  
#### <a name="to-preview-the-ribbon-control"></a>預覽功能區控制項  
  
-   在**Ribbon 編輯器工具列**，按一下 **測試 Ribbon**。  
  
## <a name="see-also"></a>請參閱  
 [功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)

