---
title: 樹狀控制項的父和子項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c56885300b05cfb038dd1a8484ae57648bf9357
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208428"
---
# <a name="tree-control-parent-and-child-items"></a>樹狀目錄控制項的父和子項目
樹狀結構控制項中的任何項目 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 可以有子項目，稱為子項目，與它相關聯的清單。 有一個或多個子項目的項目稱為父項目。 子項目會在其父項目下方以縮排顯示，表示其附屬於父代。 沒有父代的項目會位於階層架構的頂端並稱為根項目。  
  
 在任何指定時間內，父項目的子項目清單狀態可以是展開或摺疊。 當其狀態為展開時，表示子項目會顯示在父項目下方。 當它摺疊時，則不會顯示子項目。 清單會自動切換展開和摺疊狀態當使用者按兩下父項目或父代是否**TVS_HASBUTTONS**樣式，當使用者按一下按鈕與父項目相關聯。 應用程式可以展開或摺疊子項目，方法是使用[展開](../mfc/reference/ctreectrl-class.md#expand)成員函式。  
  
 將項目新增至樹狀目錄控制項的藉由呼叫[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成員函式。 此函式傳回的控制代碼**HTREEITEM**型別，可唯一識別項目。 在加入項目時，您必須指定新項目之父項目的控制代碼。 如果您指定**NULL**或**TVI_ROOT**而不是在父項目控制代碼值[TVINSERTSTRUCT](/windows/desktop/api/commctrl/ns-commctrl-tagtvinsertstructa)結構或*hParent*參數項目會加入做為根項目。  
  
 樹狀目錄控制項會傳送[TVN_ITEMEXPANDING](/windows/desktop/Controls/tvn-itemexpanding)父項目的子項目清單將要展開或摺疊時的通知訊息。 通知為您提供一個機會，可防止變更或根據子項目清單狀態設定父項目的任何屬性。 變更清單的狀態之後, 樹狀目錄控制項會傳送[TVN_ITEMEXPANDED](/windows/desktop/Controls/tvn-itemexpanded)通知訊息。  
  
 當子項目清單展開時，它會以相對於父項目的位置進行縮排。 您可以透過設定縮排的量[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)成員函式，或是擷取所使用的目前工作量[GetIndent](../mfc/reference/ctreectrl-class.md#getindent)成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

