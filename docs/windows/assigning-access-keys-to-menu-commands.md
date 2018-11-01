---
title: 指定便捷鍵至功能表命令 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
ms.openlocfilehash: 7a3302f7744bf5c3a0cbaac96de04d9f649fac10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587326"
---
# <a name="assigning-access-keys-to-menu-commands-c"></a>指定便捷鍵至功能表命令 （c + +）

在 c + + 專案中，您可以加入您的功能表和功能表命令指派便捷鍵 （助憶鍵，可讓使用者選取 [鍵盤] 功能表）。

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>為功能表命令指派便捷鍵 (快速鍵)

1. 輸入連字號 (`&`) 內的功能表名稱或命令名稱，即可該字母指定為對應的便捷鍵的字母前面。 例如"& 檔案"集**Alt**+**F**做為快速鍵的**檔案**撰寫的 Microsoft Windows 應用程式中的功能表。

   功能表項目會顯示提示告知其中一個字母已被指派為快速鍵。 緊接在 & 符號之後的字母會加上底線 (取決於作業系統)。

   > [!NOTE]
   > 請在您的功能表上按一下滑鼠右鍵，確定功能表上的所有便捷鍵皆未重複，然後從捷徑功能表中選擇 [檢查助憶鍵]  。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)