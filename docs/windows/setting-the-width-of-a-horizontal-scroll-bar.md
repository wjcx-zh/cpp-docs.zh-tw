---
title: "設定水平捲軸的寬度 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls, scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars, displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars, width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97015327803a82161e8dc121e8085e63b791acdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>設定水平捲軸的寬度
當您使用 MFC 類別的對話方塊中新增具有水平捲軸的清單方塊時，捲軸不會自動出現在您的應用程式。  
  
### <a name="to-make-the-scroll-bar-appear"></a>若要讓捲軸出現  
  
1.  藉由呼叫設定最寬的項目最大寬度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)程式碼中。  
  
     沒有設定這個值，捲軸不會出現，即使當清單方塊中的項目會比方塊寬。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
 需求  
  
 MFC  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)

