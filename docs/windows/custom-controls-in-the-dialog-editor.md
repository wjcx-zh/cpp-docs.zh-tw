---
title: 對話方塊編輯器中自訂控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c2bca249958e4d25ab5377540525da34802ac04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="custom-controls-in-the-dialog-editor"></a>在對話方塊編輯器中自訂控制項
對話方塊編輯器可讓您使用現有的 「 自訂 」 或 「 使用者 」 控制項在對話方塊範本中。  
  
> [!NOTE]
>  自訂控制項，這一點而言為不 ActiveX 控制項與混淆。 ActiveX 控制項已有時也稱為 OLE 自訂控制項。 此外，請勿混淆這些控制項與主控描繪控制項視窗中。  
  
 這項功能被為了讓您使用所提供的 Windows 之外的控制項。 在執行階段，其控制項是相關聯的視窗類別 （相同做為 c + + 類別）。 較常見的方式來完成相同的工作是安裝在對話方塊中的任何控制項，例如，靜態控制項。 然後會在執行階段，在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式，移除該控制項，並取代您自己的自訂控制項。  
  
 這是舊的技巧。 目前建議您在大部分情況下撰寫 ActiveX 控制項或 Windows 通用控制項子類別。  
  
 對於這些自訂控制項，您僅限於：  
  
-   在對話方塊中設定的位置。  
  
-   輸入標題。  
  
-   用來識別控制項的視窗類別 （應用程式程式碼必須登錄此控制項使用這個名稱） 的名稱。  
  
-   輸入 32 位元的十六進位值，設定控制項的樣式。  
  
-   設定延伸的樣式。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)

