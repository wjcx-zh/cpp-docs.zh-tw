---
title: 將命令加入至功能表 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3564a808d39aa81ed3b45a1bc5812b285199e04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="adding-commands-to-a-menu"></a>將命令加入至功能表
### <a name="to-add-commands-to-a-menu"></a>將命令新增至功能表  
  
1.  [建立功能表](../windows/creating-a-menu.md)。  
  
2.  按一下功能表名稱，例如，File。  
  
     每個功能表會展開並公開命令的新項目方塊。 例如，您可以將 New、Open 和 Close 等命令新增至 [檔案] 功能表。  
  
3.  在新的項目方塊中，輸入新功能表命令的名稱。  
  
    > [!NOTE]
    >  您輸入的文字會出現在功能表編輯器和**標題**方塊中[屬性 視窗](/visualstudio/ide/reference/properties-window)。 您可以在任一位置編輯新功能表的屬性。  
  
    > [!TIP]
    >  您可以定義可讓使用者選取功能表命令的助憶鍵 (熱鍵)。 在字母前面輸入連字號 (&)，將其指定為助憶鍵。 使用者可以輸入該字母來選取功能表命令。  
  
4.  在 [屬性] 視窗中，選取要套用的功能表命令屬性。 如需詳細資訊，請參閱[功能表命令屬性](../windows/menu-command-properties.md)。  
  
5.  在**提示**方塊中 [屬性] 視窗中，輸入您想要在您的應用程式狀態列中顯示的提示字串。  
  
     這會在字串資料表中建立具有相同資源識別碼的項目，做為您建立的功能表命令。  
  
    > [!NOTE]
    >  提示只能套用至功能表項目**快顯**屬性**True**。 例如，如果最上層功能表項目有子功能表項目，就可以有提示。 提示的目的是指出當使用者按一下功能表項目時會發生什麼情況。  
  
6.  按**ENTER**完成功能表命令。  
  
     已選取新項目方塊，您就可以建立其他的功能表命令。  
  

  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [功能表編輯器](../windows/menu-editor.md)   
