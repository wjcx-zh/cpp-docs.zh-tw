---
title: "變更多個快速鍵屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fbe5ab2202da457c8970d84d304ec97fdedd4a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-properties-of-multiple-accelerator-keys"></a>變更多個快速鍵屬性
### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要變更多個快速鍵屬性  
  
1.  它在圖示上按兩下開啟快速鍵對應表[資源檢視](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  選取您想要變更按住的快速鍵**CTRL**鍵，並按一下每個。  
  
3.  移至[屬性 視窗](/visualstudio/ide/reference/properties-window) 並輸入您想要將所有選取的加速器共用的值。  
  
    > [!NOTE]
    >  每個修飾詞值會顯示為 [屬性] 視窗中的布林值屬性。 如果您變更[修飾詞](../windows/accelerator-modifier-property.md)[屬性] 視窗快速鍵對應表中的值視為先前有任何修飾詞的額外功能的新修飾詞。 因為這個緣故，如果您設定任何修飾詞的值，您必須將它們，以確保每個快速鍵都共用相同的修飾詞設定所有設定。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [編輯快速鍵對應表](../windows/editing-accelerator-tables.md)   
 [快速鍵編輯器](../windows/accelerator-editor.md)