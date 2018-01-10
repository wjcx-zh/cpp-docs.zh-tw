---
title: "建立工具列按鈕的工具提示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor, creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b5bb25a14d68c01c25d9242df89c1183511ca83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-tool-tip-for-a-toolbar-button"></a>建立工具列按鈕的工具提示
### <a name="to-create-a-tool-tip"></a>若要建立工具提示  
  
1.  選取工具列按鈕。  
  
2.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，請在**提示**屬性欄位中，新增 [狀態] 列; 訊息之後，將按鈕的描述，加入 \n 和工具提示的名稱。  
  
 工具提示的常見範例是在 WordPad 中的 [列印] 按鈕：  
  
 1. 開啟 [WordPad]。  
  
 2. 將滑鼠指標停留**列印**工具列按鈕。  
  
 3. 請注意，這個字 「 列印 」 現在浮動窗格下滑鼠指標。  
  
 4. 查看狀態列 （位於 [WordPad] 視窗的最底部）-請注意，它現在顯示文字"會列印使用中文件 」。  
  
 在步驟 3 中的 「 列印 」 是 「 工具提示名稱 」，而 「 列印使用中文件' 步驟 4 的 」 描述的 [狀態] 列按鈕。 」  
  
 如果您要使用此效果**工具列**編輯器 中，設定**提示**屬性**會列印使用中文 prompt**。  
  
> [!NOTE]
>  您可以編輯的提示文字使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 MFC 或 ATL  
  
## <a name="see-also"></a>請參閱  
 [建立、 移動和編輯工具列按鈕](../windows/creating-moving-and-editing-toolbar-buttons.md)   
 [工具列編輯器](../windows/toolbar-editor.md)

