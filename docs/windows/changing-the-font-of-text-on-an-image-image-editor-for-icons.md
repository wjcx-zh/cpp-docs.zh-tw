---
title: "將影像 （圖示影像編輯器） 上的文字字型變更 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86942af0085bf749c8e1bbbab27a9a674164da79
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>變更影像上的文字字型 (圖示影像編輯器)
下列程序是如何的範例：  
  
-   將文字加入至 Windows 應用程式中的圖示  
  
-   管理您的文字的字型  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>若要變更影像上的文字字型  
  
1.  建立 c + + Windows Form 應用程式。 如需詳細資訊，請參閱[建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。 [Windows Form 應用程式範本](http://msdn.microsoft.com/en-us/1babdebf-ab3f-4a64-a608-98499a5b9cea)，將預設名稱為 app.ico 至您的專案檔。  
  
2.  在 方案總管 中，按兩下 檔案 app.ico。 [影像編輯器](../windows/image-editor-for-icons.md)隨即開啟。  
  
3.  從**映像**功能表上，選取**工具**，然後選取 **文字工具**。 [文字工具對話方塊](../windows/text-tool-dialog-box-image-editor-for-icons.md)會出現。  
  
4.  在文字工具對話方塊中，輸入`C++`空白文字區域中。 此文字會出現在可調整大小的方塊位於 app.ico、 在 [影像編輯器] 中的左上角。  
  
5.  在 [影像編輯器] 中，將可調整大小的方塊拖曳 app.ico 中心，以改善文字的可讀性。  
  
6.  文字工具對話方塊中，按一下 [**字型**] 按鈕。 [文字工具字型對話方塊](../windows/text-tool-font-dialog-box-image-editor-for-icons.md)會出現。  
  
7.  文字工具字型對話方塊中，選取**Times New Roman**從清單中所列的可用字型**字型**清單方塊。  
  
8.  選取**粗體**從清單中列出可用的字型樣式**字型樣式**清單方塊。  
  
9. 選取**10**點可用的清單中所列的大小**大小**清單方塊。  
  
10. 按一下**確定** 按鈕。 文字工具字型對話方塊會關閉，而新字型設定會套用到您的文字。  
  
11. 按一下**關閉**文字工具對話方塊上的按鈕。 可調整文字周圍方塊就會消失從影像編輯器。  
  
## <a name="see-also"></a>另請參閱  
 [編輯圖形資源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [工具列](../windows/toolbar-image-editor-for-icons.md)

