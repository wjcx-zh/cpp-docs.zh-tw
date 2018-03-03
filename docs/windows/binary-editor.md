---
title: "二進位編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4dade674fb32615e23904e6dbaf03d6c6ee0a371
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="binary-editor"></a>二進位編輯器
> [!WARNING]
>  二進位編輯器在 Express 版中無法使用的。  
  
 二進位編輯器允許您在二進位層級，以十六進位或 ASCII 格式編輯任何資源。 您也可以使用 [[尋找命令]](/visualstudio/ide/reference/find-command) 搜尋 ASCII 字串或十六進位位元組。 請只有在需要檢視或對 Visual Studio 環境不支援的自訂資源或資源類型進行細微變更時，才使用二進位編輯器。  
  
 若要開啟二進位編輯器，首先選擇**檔案 &#124;新 &#124;檔案**從主功能表中，選取您想要編輯，然後按一下下拉箭號旁的檔案**開啟**按鈕，然後選擇**開啟 &#124;二進位編輯器**。  
  
> [!CAUTION]
>  在二進位編輯器中編輯諸如對話方塊、影像或功能表等資源，是很危險的事。 不正確的編輯可能會損毀資源，讓它在原生編輯器中無法讀取。  
  
> [!TIP]
>  使用二進位編輯器時，在許多情況下您可以按一下滑鼠右鍵，顯示資源特定命令的快顯功能表。 可用的命令取決於游標所指項目。 例如，如果在指向含有所選十六進位值的二進位編輯器時按一下，快顯功能表就會顯示 [剪下] 、[複製] 和 [貼上]  命令。  
  
 使用二進位編輯器，您可以：  
  
-   [開啟資源進行二進位編輯](../windows/opening-a-resource-for-binary-editing.md)  
  
-   [編輯二進位資料](../windows/editing-binary-data.md)  
  
-   [尋找二進位資料](../windows/finding-binary-data.md)  
  
-   [建立新的自訂或資料資源](../windows/creating-a-new-custom-or-data-resource.md)  
  
## <a name="managed-resources"></a>Managed 資源  
 您可以使用影像編輯器和 [二進位編輯器](../windows/image-editor-for-icons.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>請參閱  
 [資源編輯器](../windows/resource-editors.md)

