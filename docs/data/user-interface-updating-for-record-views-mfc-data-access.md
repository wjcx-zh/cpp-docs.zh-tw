---
title: "使用者介面更新資料錄檢視 （MFC 資料存取） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68b013f3b1211c42ffc7355df73f47f6520fac1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>記錄檢視的使用者介面更新 (MFC 資料存取)
`CRecordView`提供巡覽命令的預設使用者介面更新處理常式。 這些處理常式會自動啟用和停用功能表項目和工具列按鈕等使用者介面物件。 應用程式精靈提供標準功能表和，如果您選擇**可停駐工具列**選項，一組命令工具列按鈕。 如果您使用 `CRecordView` 建立記錄檢視類別，可能需要將類似的使用者介面物件加入應用程式。  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>使用功能表編輯器建立功能表資源  
  
1.  參考使用的詳細資訊[功能表編輯器](../windows/menu-editor.md)，使用相同的四個命令建立您自己的功能表。  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>使用圖形編輯器建立工具列按鈕  
  
1.  參考使用的詳細資訊[工具列編輯器](../windows/toolbar-editor.md)，編輯工具列資源以加入記錄巡覽命令的工具列按鈕。  
  
## <a name="see-also"></a>請參閱  
 [支援資料錄檢視的巡覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)