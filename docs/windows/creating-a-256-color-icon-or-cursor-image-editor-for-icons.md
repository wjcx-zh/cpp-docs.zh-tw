---
title: "建立 256 色圖示或游標 （圖示影像編輯器） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- 256-color palette
- cursors, color
- colors, icons
- colors, cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12baf092d432aff4ac16d00f1877128eef629e14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>建立 256 色圖示或游標 (圖示影像編輯器)
使用影像編輯器，圖示和游標可能會調整大小大 (64 × 64) 256 色調色盤可從中選擇。 建立資源之後, 會選取裝置影像樣式。  
  
### <a name="to-create-a-256-color-icon-or-cursor"></a>若要建立 256 色圖示或游標  
  
1.  在[資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇 **插入資源**從捷徑功能表。 (如果您已經有現有的映像資源在.rc 檔案中，例如資料指標中，您可以直接以滑鼠右鍵按一下**游標**資料夾，然後選取**插入游標**從捷徑功能表。)  
  
     **附註** 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入資源對話方塊](../windows/add-resource-dialog-box.md)，選取**圖示**或**游標**按一下**新增**。  
  
3.  在**映像**功能表上，按一下 **新增裝置影像**。  
  
4.  選取您想要的 256 色影像樣式。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
 **Requirements**  
  
 無  
  
## <a name="see-also"></a>另請參閱  
 [使用 256 色調色盤](../windows/using-the-256-color-palette-image-editor-for-icons.md)   
 [快速鍵](../windows/accelerator-keys-image-editor-for-icons.md)   
 [圖示和游標： 顯示裝置的影像資源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

