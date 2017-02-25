---
title: "樹狀目錄控制項的父和子項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "樹狀目錄控制項中的子項目"
  - "CTreeCtrl 類別, 父和子項目"
  - "CTreeCtrl 中的父項目"
  - "樹狀目錄控制項, 父和子項目"
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 樹狀目錄控制項的父和子項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 中的所有項目可以有關連於它的子項目清單，稱為子項目。  有一或多個子項目的項目稱為父項目。  子項目在其父項目下方顯示並縮排表示其附屬至父代。  沒有父代的項目是在階層架構的頂端並稱為根項目。  
  
 在指定的任何時間，父項目的子項目清單的狀態可以是展開或摺疊。  在這個狀態展開時，子項目在父項目下顯示。  當它摺疊時，子項目不會顯示。  當使用者按一下與父項目關連的按鈕時，清單會自動切換展開和摺疊狀態，當使用者按一下父項目或，如果父代有 **TVS\_HASBUTTONS** 樣式。  使用 [展開](../Topic/CTreeCtrl::Expand.md) 成員函式，應用程式可以展開或摺疊子系項目。  
  
 藉由呼叫 [InsertItem](../Topic/CTreeCtrl::InsertItem.md) 成員函式，您將項目加入至樹狀目錄控制項。  這個函式會傳回 **HTREEITEM** 型別的控制代碼，這可唯一識別項目。  在加入項目時，必須指定新項目的父項目的控制代碼。  如果您指定 **NULL** 和 **TVI\_ROOT** 值而非 [TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) 結構或 `hParent` 參數中的父項目控制代碼，則會將項目加入做為根項目。  
  
 表示子項目的父項目清單將要展開或摺疊時，樹狀目錄控制項傳送 [TVN\_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) 通知訊息。  通知可以防止變更或設定取決於子項目清單狀態父項目的所有屬性。  在變更清單的狀態之後，樹狀目錄控制項傳送 [TVN\_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533) 通知訊息。  
  
 當子項目清單展開時，它會相對於父項目縮排。  使用 [GetIndent](../Topic/CTreeCtrl::GetIndent.md) 成員函式或使用 [SetIndent](../Topic/CTreeCtrl::SetIndent.md) 成員函式擷取目前數量，您可以設定縮排數量。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)