---
title: 指定便捷鍵至功能表命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], checking
- menus, shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics, adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics, uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a21e5930d0d8f2fcaad79cc5cef5bc984ad8b5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="assigning-access-keys-to-menu-commands"></a>指定便捷鍵至功能表命令
您可以為您的功能表與功能表命令指派便捷鍵 (助憶鍵，可讓使用者透過鍵盤選取功能表)。  
  
### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>為功能表命令指派便捷鍵 (快速鍵)  
  
1.  在功能表名稱或命令名稱中的任一字母前輸入 &amp; 符號 (**&**)，即可該字母指定為對應的便捷鍵。 例如 "&File" 會將 ALT + F 設為您為 Microsoft Windows 所撰寫之應用程式中的 [File] 功能表的快速鍵。  
  
     功能表項目會顯示提示告知其中一個字母已被指派為快速鍵。 緊接在 & 符號之後的字母會加上底線 (取決於作業系統)。  
  
    > [!NOTE]
    >  請在您的功能表上按一下滑鼠右鍵，確定功能表上的所有便捷鍵皆未重複，然後從捷徑功能表中選擇 [檢查助憶鍵]  。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [功能表編輯器](../windows/menu-editor.md)