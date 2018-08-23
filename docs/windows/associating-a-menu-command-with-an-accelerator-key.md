---
title: 將功能表命令和快速鍵建立關聯 |Microsoft Docs
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
ms.openlocfilehash: 5b1411617df3736300536e84e07da0bb5df3a856
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599946"
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>將功能表命令和快速鍵建立關聯

常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 您可以使用 **功能表**編輯器，將相同的資源識別碼指派給功能表命令和您的應用程式快速鍵對應表中的項目。 您可以接著編輯功能表命令的 [標題](../windows/menu-command-properties.md) ，以顯示快速鍵的名稱。

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>建立功能表命令和快速鍵的關聯

1. 在 **功能表** 編輯器中，選取您想要的功能表命令。

2. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中，將快速鍵的名稱加入 [標題]  屬性中：

   - 在功能表標題後面輸入定位鍵 (\t) 的逸出序列，讓所有的功能表快速鍵都靠左對齊。

   - 輸入輔助按鍵的名稱 (**Ctrl**， **Alt**，或**Shift**) 後面接著加號 (**+**) 和名稱、 字母，或額外的索引鍵的符號。

       例如，若要指派**Ctrl**+**O**來**開啟**命令**檔案** 功能表中，您可以修改功能表命令**標題**，讓它看起來像這樣：

        ```
        &Open...\tCtrl+O
        ```

       中的功能表命令 **功能表**編輯器會更新以反映新的標題，當您輸入它。

3. 在[快速鍵](../windows/adding-an-entry-to-an-accelerator-table.md) 編輯器中 **建立快速鍵對應表項目** ，並為它指派與功能表命令相同的識別項。 請使用您認為容易記住的按鍵組合。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[將命令新增至功能表](../windows/adding-commands-to-a-menu.md)  
[功能表編輯器](../windows/menu-editor.md)