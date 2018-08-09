---
title: 開啟資源進行二進位編輯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26d1b0ae8923835b0ce06c7312fa185693c6586e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014503"
---
# <a name="opening-a-resource-for-binary-editing"></a>開啟資源進行二進位編輯
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>開啟 Windows 桌面資源進行二進位編輯  
  
1.  在 [[資源檢視]](../windows/resource-view-window.md)中，選取您要編輯的特定資源檔。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  以滑鼠右鍵按一下資源，然後從捷徑功能表按一下 [開啟二進位資料]  。  
  
    > [!NOTE]
    >  如果您使用[資源檢視](../windows/resource-view-window.md)視窗開啟，Visual Studio 無法辨識格式 （例如 RCDATA 或自訂資源），該資源的資源會自動以開啟**二進位**編輯器。  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>開啟 Managed 資源進行二進位編輯  
  
1.  在 [**方案總管] 中**，選取您想要編輯的特定資源檔。  
  
2.  以滑鼠右鍵按一下資源，然後從捷徑功能表選擇 [開啟方式]  。  
  
3.  在 [開啟方式]  對話方塊中，選擇 [二進位編輯器] 。  
  
    > [!NOTE]
    >  您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。  
  
    > [!NOTE]
    >  如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。   
  
 ![二進位編輯器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
二進位編輯器中所顯示之對話方塊的二進位資料  
  
 二進位編輯器中只會表示特定 ASCII 值 (0x20 到 0x7E)。 擴充字元會在二進位編輯器的 [ASCII 值] 區段 (右窗格) 中顯示為句號。 「可列印」字元是 ASCII 值 32 到 126。  
  
> [!NOTE]
>  如果您想要使用**二進位**編輯器已經在另一個編輯器視窗中，編輯的資源上先關閉其他編輯器視窗。  
  
## <a name="requirements"></a>需求  
 無  
  
## <a name="see-also"></a>另請參閱  
 [Binary Editor](binary-editor.md)