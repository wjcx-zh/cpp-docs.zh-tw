---
title: "定義助憶鍵 （便捷鍵） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls, mnemonics
- access keys [C++], checking
- mnemonics, checking for duplicate
- mnemonics
- mnemonics, dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 167947e51ed773f765432148cbe879c926c57d5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="defining-mnemonics-access-keys"></a>定義助憶鍵 (便捷鍵)
一般來說，鍵盤使用者輸入的焦點一個控制項之間移動的對話方塊中使用 TAB 和方向鍵金鑰。 不過，您可以定義便捷鍵 （助憶鍵，或按一下 容易記住名稱），可讓使用者選擇的控制項按單一索引鍵。  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定義具有可見的標題 （按鈕、 核取方塊和選項按鈕） 的控制項的便捷鍵  
  
1.  選取對話方塊上的控制項。  
  
2.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，請在**標題**屬性中，輸入控制項中，輸入 & 符號的新名稱 (**&**) 您要做為的字母前面該控制項的便捷鍵。 例如，`&Radio1`。  
  
3.  按 **Enter** 鍵。  
  
     在顯示來表示的存取金鑰，例如，標題會出現底線**R**adio1。  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定義沒有可見標題控制項的便捷鍵  
  
1.  請使用控制項的標題**靜態文字**控制[工具箱](/visualstudio/ide/reference/toolbox)。  
  
2.  在靜態文字標題中，輸入以連字號 (**&**) 您要作為便捷鍵的字母前面。  
  
3.  請確定靜態文字控制項前面的控制項之前的定位順序。  
  
 在對話方塊中的所有便捷鍵應該都是唯一的。  
  
#### <a name="to-check-for-duplicate-access-keys"></a>若要檢查有重複的便捷鍵  
  
1.  在**格式**功能表上，按一下 **檢查助憶鍵**。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)

