---
title: 樹狀目錄控制項目標籤 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e016093e2dcde68fcc01691c4877841d648321fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207460"
---
# <a name="tree-control-item-labels"></a>樹狀目錄控制項目標籤
您通常會指定項目的標籤的文字時將項目加入至樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 `InsertItem`成員函式可以傳遞[TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema)結構，定義項目的屬性，包括字串，包含標籤的文字。 `InsertItem` 有數個多載，可以使用各種不同的參數組合來呼叫。  
  
 樹狀目錄控制項配置記憶體來儲存每個項目;項目標籤的文字會佔用記憶體的重要部分。 如果您的應用程式會維護一份在樹狀結構控制項中的字串，您可以藉由指定減少控制項的記憶體需求**LPSTR_TEXTCALLBACK**中的值*pszText* 的成員`TV_ITEM`或*lpszItem*而不是將實際的字串傳遞至樹狀結構控制項中的參數。 使用**LPSTR_TEXTCALLBACK**會導致從應用程式擷取的項目標籤的文字，每當需要重新繪製的項目樹狀目錄控制項。 若要擷取文字，樹狀目錄控制項會傳送[TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo)通知訊息，其中包含的位址[2&AMP;GT;NMTVDISPINFO&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa)結構。 您必須藉由設定適當的成員，包含結構的回應。  
  
 樹狀目錄控制項中，會使用從建立樹狀結構控制項中的程序的堆積配置的記憶體。 樹狀結構控制項中的項目數目上限為基礎的堆積中可用的記憶體數量。 每個項目會使用 64 個位元組。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

