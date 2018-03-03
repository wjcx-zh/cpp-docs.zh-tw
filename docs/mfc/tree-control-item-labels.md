---
title: "樹狀目錄控制項目標籤 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d9baece3986b00aa2fbcea2b4b64217618834a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-item-labels"></a>樹狀目錄控制項目標籤
您通常會指定項目的標籤時項目加入至樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 `InsertItem`成員函式可以傳遞[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)結構，定義項目的屬性，包括字串，包含標籤的文字。 `InsertItem`有數個多載，可以使用各種不同的參數組合呼叫。  
  
 樹狀目錄控制項配置記憶體來儲存每個項目。項目標籤的文字會佔用記憶體的重要部分。 如果您的應用程式會維護一份在樹狀目錄控制項中的字串，您還可以減少記憶體需求的控制項，藉由指定**LPSTR_TEXTCALLBACK**值**pszText** 的成員`TV_ITEM`或`lpszItem`參數，而不是實際的字串傳遞至樹狀目錄控制項。 使用**LPSTR_TEXTCALLBACK**導致樹狀結構控制項項目需要重新繪製時，從應用程式擷取的項目標籤的文字。 若要擷取文字，樹狀目錄控制項會傳送[TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518)通知訊息，包括位址[NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418)結構。 您必須藉由設定適當的成員包含結構的回應。  
  
 樹狀目錄控制項使用從建立樹狀結構控制項中的程序堆積配置額外的記憶體。 樹狀結構控制項中的項目數目上限為基礎的堆積中可用的記憶體數量。 每個項目需要 64 位元。  
  
## <a name="see-also"></a>請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

