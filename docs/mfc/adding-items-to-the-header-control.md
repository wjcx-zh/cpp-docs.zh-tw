---
title: "將項目加入至標題控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 792c956d73808ef50308f8e14066f74021cc84b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="adding-items-to-the-header-control"></a>將項目加入至標題控制項
建立標題控制項之後 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 在其父視窗中，加入許多 「 標頭項目 」 所需： 通常每欄一個。  
  
### <a name="to-add-a-header-item"></a>若要加入標題項目  
  
1.  準備[HD_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247)結構。  
  
2.  呼叫[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem)，傳遞結構。  
  
3.  針對其他項目重複步驟 1 和 2。  
  
 如需詳細資訊，請參閱[項目加入至標題控制項](http://msdn.microsoft.com/library/windows/desktop/bb775238)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

