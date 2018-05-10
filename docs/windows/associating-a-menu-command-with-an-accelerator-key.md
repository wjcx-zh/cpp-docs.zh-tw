---
title: 建立功能表命令和快速鍵的關聯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4f1aa4b80aec2e7c16485c08d2505695b21f4d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>將功能表命令和快速鍵建立關聯
常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 若要達成這項目的，請使用功能表編輯器，將相同的資源識別項指派給功能表命令與應用程式快速鍵對應表中的項目。 您可以接著編輯功能表命令的 [標題](../windows/menu-command-properties.md) ，以顯示快速鍵的名稱。  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>建立功能表命令和快速鍵的關聯  
  
1.  在 **功能表** 編輯器中，選取您想要的功能表命令。  
  
2.  在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，將快速鍵的名稱加入 [標題]  屬性中：  
  
    -   在功能表標題後面輸入定位鍵 (\t) 的逸出序列，讓所有的功能表快速鍵都靠左對齊。  
  
    -   輸入輔助按鍵 (例如**CTRL**、 **ALT**或 **SHIFT**) 的名稱，後面接著加號 (**+**) 和額外按鍵的名稱、字母或符號。  
  
         例如，若要將 **CTRL+O** 指派給 [檔案]  功能表的 [開啟舊檔]  命令，您可以修改功能表命令的 [標題]  ，讓它變成：  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         功能表編輯器中的功能表命令將會更新，以反映您輸入的新標題。  
  
3.  在[快速鍵](../windows/adding-an-entry-to-an-accelerator-table.md) 編輯器中 **建立快速鍵對應表項目** ，並為它指派與功能表命令相同的識別項。 請使用您認為容易記住的按鍵組合。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [將命令加入至功能表](../windows/adding-commands-to-a-menu.md)   
 [功能表編輯器](../windows/menu-editor.md)