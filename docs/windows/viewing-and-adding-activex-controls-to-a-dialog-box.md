---
title: "檢視和對話方塊中加入 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.activex
dev_langs: C++
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- Insert ActiveX Control command
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 053e03717558e7eab1c92e1a50e6e3ce85a9fa9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box"></a>檢視 ActiveX 控制項以及將 ActiveX 控制項加入對話方塊
Visual Studio 可讓您在您的對話方塊中插入 ActiveX 控制項。  
  
### <a name="to-see-the-activex-controls-you-have-available"></a>查看您可使用的 ActiveX 控制項  
  
1.  在 [對話方塊] 編輯器中開啟對話方塊。  
  
2.  在對話方塊主體中的任意處按一下滑鼠右鍵。  
  
3.  在捷徑功能表上，按一下 [插入 ActiveX 控制項] 。  
  
     [[插入 ActiveX 控制項] 對話方塊](../windows/insert-activex-control-dialog-box.md) 會隨即出現，顯示您系統上所有的 ActiveX 控制項。 ActiveX 控制項檔案的路徑會顯示在對話方塊的底部。  
  
### <a name="to-add-an-activex-control-to-a-dialog-box"></a>在對話方塊中加入 ActiveX 控制項  
  
1.  在 [[插入 ActiveX 控制項] 對話方塊](../windows/insert-activex-control-dialog-box.md)中，選取您要加入對話方塊中的控制項，然後按一下 [確定] 。  
  
     該控制項會出現在對話方塊中。您可以像處理其他控制項般地加以編輯，或為其建立處理常式。  
  
    > [!NOTE]
    >  您可以將 ActiveX 控制項加入 [[工具箱] 視窗](/visualstudio/ide/reference/toolbox)。 如需詳細資訊，請參閱 [管理 [工具箱] 中的項目和索引標籤](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)。  
  
    > [!CAUTION]
    >  在您的系統上散發所有的 ActiveX 控制項可能不合法。 請參閱安裝這些控制項之軟體的授權合約，或連絡軟體公司。  
  
     您可以將控制項置於 [工具箱] 視窗內，以便於存取。 如需詳細資訊，請參閱 [自訂 [工具箱] 對話方塊](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
 **Requirements**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)

