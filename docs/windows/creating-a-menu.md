---
title: 建立功能表 |Microsoft Docs
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
- mnemonics, associating menu items
- menus, associating commands with mnemonic keys
- menus, creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93788240ae90463c430a2d53df7e3e7f087b2c97
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596730"
---
# <a name="creating-a-menu"></a>建立功能表

> [!NOTE]
> **資源視窗**不適用於 Express 版本。

### <a name="to-create-a-standard-menu"></a>建立標準功能表

1. 按一下 [ **檢視** ] 功能表上的 [ **資源檢視** ]，然後以滑鼠右鍵按一下 [ **功能表** ] 標題並選擇 [ **加入資源**]。 選擇 [ **功能表**]。

2. 在功能表列上選取 [新增項目]  方塊 (有「在這裡輸入」的矩形)。

   ![功能表編輯器中的新項目方塊](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")  
新增項目方塊

3. 輸入新功能表的名稱，例如「檔案」。

   您輸入的文字會出現在 **功能表** 編輯器和 **[屬性] 視窗** 中的 [[標題]](/visualstudio/ide/reference/properties-window)方塊中。 您可以在任一位置編輯新功能表的屬性。

   一旦在功能表列上指定了新的功能表名稱，[新增項目] 方塊就會右移 (讓您加入另一個功能表)，並在第一個功能表底下開啟另一個 [新增項目] 方塊，讓您加入功能表命令。

   ![展開新的項目方塊](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")  
輸入功能表名稱之後，[新增項目] 方塊的焦點會移位

   > [!NOTE]
   > 若要建立單一項目 功能表的功能表列上，設定**快顯**屬性設**False**。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[功能表編輯器](../windows/menu-editor.md)