---
title: 將命令加入至功能表 |Microsoft Docs
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
ms.openlocfilehash: c0c744e920c71b74d9296e6961add704435658fe
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644725"
---
# <a name="adding-commands-to-a-menu"></a>將命令加入至功能表
### <a name="to-add-commands-to-a-menu"></a>將命令新增至功能表  
  
1.  [建立功能表](../windows/creating-a-menu.md)。  
  
2.  按一下功能表名稱，例如**檔案**。  
  
     每個功能表會展開並公開命令的新項目方塊。 比方說，您可以將命令加入**新增**，**開放**，並**關閉**至**檔案**功能表。  
  
3.  在新的項目方塊中，輸入新功能表命令的名稱。  
  
    > [!NOTE]
    >  您輸入的文字會出現在 **功能表** 編輯器和 **[屬性] 視窗** 中的 [[標題]](/visualstudio/ide/reference/properties-window)方塊中。 您可以在任一位置編輯新功能表的屬性。  
  
    > [!TIP]
    >  您可以定義可讓使用者選取功能表命令的助憶鍵 (熱鍵)。 輸入連字號 (`&`) 將它指定為助憶鍵的字母前面。 使用者可以輸入該字母來選取功能表命令。  
  
4.  在 **屬性**視窗中，選取功能表命令時套用的屬性。 如需詳細資訊，請參閱 <<c0> [ 功能表命令屬性](../windows/menu-command-properties.md)。  
  
5.  在 [**提示字元**方塊中**屬性**] 視窗中，輸入您想要在您的應用程式狀態列中顯示的提示字串。  
  
     這會在字串資料表中建立具有相同資源識別碼的項目，做為您建立的功能表命令。  
  
    > [!NOTE]
    >  提示只能套用至功能表項目**快顯**屬性 **，則為 True**。 例如，如果最上層功能表項目有子功能表項目，就可以有提示。 目的**提示**表示會發生什麼情況是如果使用者按一下功能表項目。  
  
6.  按下**Enter**完成功能表命令。  
  
     已選取新項目方塊，您就可以建立其他的功能表命令。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [功能表編輯器](../windows/menu-editor.md)   