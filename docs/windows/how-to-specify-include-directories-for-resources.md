---
title: "如何： 指定資源的 Include 目錄 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- directories [C++], specifying include paths for resources
- include files, specifying for resources
- resources [Visual Studio], including in projects
ms.assetid: d6a7c0f6-4810-4bb0-b4b7-7d2476a20ca2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ddaa4bf15894b1afe4edec952b5c707a1dcfac0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-specify-include-directories-for-resources"></a>如何：指定資源的 Include 目錄
### <a name="to-specify-include-directories-for-a-specific-rc-file"></a>指定特定 RC 檔的 Include 目錄  
  
1.  以滑鼠右鍵按一下方案總管 中的.rc 檔，然後選取**屬性**從捷徑功能表。  
  
2.  在**屬性頁**對話方塊中，按一下 **資源**左窗格中的節點，然後指定其他的 include 目錄中的**其他 include 目錄**屬性。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index).NET Framework 開發人員指南中。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 使用資源以利用 ASP.NET進行當地語系化](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [資源包含對話方塊](../windows/resource-includes-dialog-box.md)   
 [TN035： 使用 Visual c + + 的多個資源檔和標頭檔](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)   
 [符號： 資源識別項](../windows/symbols-resource-identifiers.md)   
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)