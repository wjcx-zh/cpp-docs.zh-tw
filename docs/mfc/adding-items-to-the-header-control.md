---
title: 將項目加入至標題控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d64265a94df2770e3a234ab992130b4809f9e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342731"
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

