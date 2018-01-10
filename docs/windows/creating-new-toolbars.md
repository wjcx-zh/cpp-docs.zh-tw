---
title: "建立新的工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.toolbar
dev_langs: C++
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor, creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4315d101f194b9c0ff1a66b9e7cf81dc778cf372
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-new-toolbars"></a>建立新的工具列
### <a name="to-create-a-new-toolbar"></a>若要建立新的工具列  
  
1.  在**資源**檢視，以滑鼠右鍵按一下.rc 檔，然後選擇 **加入資源**從捷徑功能表。 (如果您在.rc 檔中有現有的工具列上，您可以直接以滑鼠右鍵按一下**工具列**資料夾，然後選取**插入工具列**從捷徑功能表。)  
  
     **附註** 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**加入資源**對話方塊中，選取**工具列**中**資源類型**清單，然後按一下**新增**。  
  
     如果旁邊出現一個加號 （+）**工具列**資源類型，表示工具列範本可供使用。 按一下加號，展開範本的清單，選取的範本，然後按一下**新增**。  
  
     \-或-  
  
3.  [將現有點陣圖轉換成工具列](../windows/converting-bitmaps-to-toolbars.md)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 MFC 或 ATL  
  
## <a name="see-also"></a>請參閱  
 [工具列編輯器](../windows/toolbar-editor.md)

