---
title: 版本資訊編輯器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version.F1
dev_langs:
- C++
helpviewer_keywords:
- Version Information editor, about Version Information editor
- editors, Version Information
- resource editors, Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 76a76dbb3d8b41c2366f354f9c3c8d66ccc3743f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="version-information-editor"></a>版本資訊編輯器
版本資訊包含公司和產品識別碼、產品版本號碼，以及版權和商標通知。 您可以使用版本資訊編輯器建立和維護這項資料，將之儲存在版本資訊資源中。 應用程式不需要版本資訊資源，但這卻是收集應用程式識別資訊的好地方。 安裝程式 API 也使用版本資訊。  
  
 版本資訊資源有一個上層區塊以及一或多個下層區塊：頂端是單一固定的資訊區塊，底部是一或多個版本資訊區塊 (適用於其他語言和/或字元集)。 上層區塊有可編輯的數值方塊和可選取的下拉式清單。 下層區塊只有可編輯的文字方塊。  
  
> [!NOTE]
>  Windows 標準是只能有一個版本資源，名為 VS_VERSION_INFO。  
  
 版本資訊編輯器可讓您：  
  
-   [編輯版本資訊資源內的字串](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [加入另一種語言的版本資訊 (新增版本資訊區塊)](../windows/adding-version-information-for-another-language.md)  
  
-   [刪除版本資訊區塊](../windows/deleting-a-version-information-block.md)  
  
-   [從您的程式內存取版本資訊](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  使用版本資訊編輯器時，在許多情況下您可以按一下滑鼠右鍵，顯示資源特定命令的快顯功能表。 例如，如果在指向區塊標頭項目時按一下，快顯功能表就會顯示 [新增版本區塊資訊] 和 [刪除版本區塊資訊] 命令。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [資源編輯器](../windows/resource-editors.md)   
 [功能表與其他資源](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

