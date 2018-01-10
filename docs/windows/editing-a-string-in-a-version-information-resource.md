---
title: "編輯版本資訊資源內的字串 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.version
dev_langs: C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5add7bfb11b1c416853bb10ddbb2956885e181ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="editing-a-string-in-a-version-information-resource"></a>編輯版本資訊資源內的字串
### <a name="to-edit-a-string-in-a-version-information-resource"></a>編輯版本資訊資源內的字串  
  
1.  按一下並選取項目，然後再按一次開始編輯。 直接在版本資訊表或 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)中進行變更。 您所做的變更會反映在這兩個位置。  
  
     **注意** 在版本資訊編輯器中編輯 **FILEFLAGS** 機碼時，您會發現無法設定 .rc 檔的 **Debug**、 **Private Build**或 **Special Build** 屬性 (位於 [屬性] 視窗中)：  
  
    -   版本資訊編輯器會根據 **_DEBUG** 組建旗標，利用資源指令碼中的 #ifdef 來設定 **Debug** 屬性。  
  
    -   如果 **Private Build** 機碼在版本資訊表中已設定 [值]  ，則 **FILEFLAGS** 機碼的對應 **Private Build** 屬性 (位於 [屬性] 視窗中) 將會是 **True**。 如果 [值]  是空的，則該屬性為 **False**。 同樣地， **Special Build** 機碼 (位於版本資訊表中) 會繫結至 **FILEFLAGS** 機碼的 **Special Build** 屬性。  
  
 您可以按一下 [機碼] 或 [值] 欄位標題，來排序字串區塊的資訊順序。 這些標題會自動依照選取的順序重新排列資訊。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [版本資訊編輯器](../windows/version-information-editor.md)   
 [版本資訊 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

