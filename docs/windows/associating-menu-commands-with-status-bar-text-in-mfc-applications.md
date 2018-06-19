---
title: 將功能表命令和 MFC 應用程式中的狀態列文字建立關聯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars, associating menu items
- menus, status bar text
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17326bdb8fe01c9ad329db0a6c7e8178fdbb25e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864238"
---
# <a name="associating-menu-commands-with-status-bar-text-in-mfc-applications"></a>將功能表命令和 MFC 應用程式內的狀態列文字建立關聯
您的應用程式可以針對使用者可能選取的每一個功能表命令顯示描述性文字。 做法是使用 [屬性] 視窗中的 [ **提示** ] 屬性，將文字字串指派給每一個功能表命令。 如果您在 [字串表](../windows/string-editor.md) 中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。  
  
### <a name="to-associate-a-menu-command-with-a-status-bar-text-string"></a>若要建立功能表命令與狀態列文字字串的關聯  
  
1.  在 [ **功能表** ] 編輯器中，選取功能表命令。  
  
2.  在 [屬性視窗](/visualstudio/ide/reference/properties-window)的 [ **提示** ] 方塊中，輸入相關聯的狀態列文字。  
  

  
 **需求**  
  
 MFC  
  
## <a name="see-also"></a>另請參閱  
 [字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [將命令加入至功能表](../windows/adding-commands-to-a-menu.md)   
 [功能表編輯器](../windows/menu-editor.md)