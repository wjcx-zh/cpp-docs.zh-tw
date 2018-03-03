---
title: "將值加入至下拉式方塊控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [Visual Studio], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- controls [C++], testing values in combo boxes
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9125ad60648f6f867e1214763a6af164d0239a04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-values-to-a-combo-box-control"></a>將值加入至下拉式方塊控制項
您可以將值加入至下拉式方塊控制項，只要您有開啟的對話方塊編輯器。  
  
> [!TIP]
>  最好將所有的值加入至下拉式方塊*之前*大小的方塊，在對話方塊編輯器中，或您可能會截斷應該會出現在下拉式控制項中的文字。  
  
#### <a name="to-enter-values-into-a-combo-box-control"></a>若要將下拉式方塊控制項中輸入值  
  
1.  按一下它，選取下拉式方塊控制項。  
  
2.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，向下捲動至**資料**屬性。  
  
    > [!NOTE]
    >  如果您要顯示屬性類型，分組**資料**會出現在**其他**屬性。  
  
3.  值區域中按一下**資料**屬性並輸入您的資料值，並以分號分隔。  
  
    > [!NOTE]
    >  因為空間干擾下拉式清單中的字母排序，請不要將值之間的空格。  
  
4.  按一下**Enter**當您完成新增的值。  
  
 放大下拉式方塊的下拉部分的資訊，請參閱[設定下拉式方塊和下拉式清單中其大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。  
  
> [!NOTE]
>  您無法將值加入至 Win32 專案使用此程序 (**資料**屬性灰色 Win32 專案)。 Win32 專案不需要加入這項功能的程式庫，因為您必須以程式設計方式將值加入至 Win32 專案與下拉式方塊中。  
  
#### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在下拉式方塊中測試值的外觀  
  
1.  在輸入中的值之後**資料**屬性中，按一下**測試**按鈕[對話方塊編輯器工具列](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。  
  
     請嘗試往下捲動整個值清單。 完全依照其輸入值會出現**資料**屬性 視窗中的屬性。 沒有任何拼字檢查或大小寫。  
  
     按 esc 鍵返回對話方塊編輯器。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)

