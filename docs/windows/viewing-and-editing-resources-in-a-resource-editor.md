---
title: 檢視和編輯資源在資源編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resourceview
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- Resource View pane
- layouts, previewing resource
- code, viewing resources
- resource editors, viewing resources
- .rc files, viewing resources
- resources [Visual Studio], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97816db8075d04b6d05950bb65c25aa12382b728
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646926"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>在資源編輯器內檢視和編輯資源
每個資源類型具有該資源類型的特定資源編輯器。 您可以重新排列、 調整大小、 新增控制項和功能，或修改其資源使用相關聯的編輯器的外觀。 您也可以編輯中的資源[文字格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)並[二進位格式](../windows/opening-a-resource-for-binary-editing.md)。  
  
 某些資源類型是個別的檔案，可以匯入和使用各種方式;這些包括點陣圖、 圖示、 游標、 工具列和 html 檔案。 這類資源的檔案名稱，以及[資源識別元](../windows/symbols-resource-identifiers.md)。 其他項目，例如對話方塊、 功能表和 Win32 專案中的字串資料表存在於只為一部分的資源指令碼 (.rc) 檔或資源範本 (.rct) 檔。  
  
> [!NOTE]
>  資源的屬性[可以使用 [屬性] 視窗來修改](../windows/changing-the-properties-of-a-resource.md)。  
  
## <a name="win32-resources"></a>Win32 資源  
 您可以存取中的 Win32 資源[資源檢視](../windows/resource-view-window.md)窗格。  
  
### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在資源編輯器中檢視的 Win32 資源  
  
1.  選取 **資源檢視**從**檢視**功能表。  
  
2.  如果資源檢視 視窗不是最上層視窗，按一下**資源檢視**將它顯示在頂端的索引標籤。  
  
3.  從 [資源] 檢視中，展開包含您想要檢視的資源的專案的資料夾。 例如，如果您想要檢視的對話方塊資源，依序展開 [對話方塊] 資料夾。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
4.  按兩下 [資源，例如 IDD_ABOUTBOX]。  
  
     資源會在適當的編輯器中開啟。 比方說，對話方塊資源，資源會開啟對話方塊編輯器內。  
  
     您也可以[檢視 （資源指令碼）.rc 檔中的資源，而不需要開啟任何專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
### <a name="to-delete-an-existing-win-32-resource"></a>若要刪除現有的 Win 32 資源  
  
1.  在 **資源檢視**，依序展開 資源類型的節點。  
  
2.  以滑鼠右鍵按一下您想要刪除，然後選擇 的資源**刪除**從捷徑功能表。  
  
    > [!NOTE]
    >  您可以刪除資源，當您在專案外部的文件視窗中開啟.rc 檔時，請使用相同的捷徑功能表命令。  
  
## <a name="resources-in-managed-projects"></a>在 Managed 專案中的資源  
 因為 managed 的專案不會使用資源指令碼檔案，您必須開啟您的資源**方案總管 中**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>若要在資源編輯器中檢視受管理的資源  
  
1.  在 [**方案總管] 中**，連按兩下該資源，例如 Bitmap1.bmp。  
  
     資源會在適當的編輯器中開啟。  
  
### <a name="to-delete-an-existing-managed-resource"></a>若要刪除現有的受控的資源  
  
1.  在 **方案總管**，以滑鼠右鍵按一下您想要刪除，然後選擇 的資源**刪除**快顯功能表中。  
  
### <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>另請參閱  
 [資源編輯器](../windows/resource-editors.md)