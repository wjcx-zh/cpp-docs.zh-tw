---
title: "樹狀目錄控制項目狀態概觀 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 項目狀態"
  - "狀態, CTreeCtrl 項目"
  - "樹狀目錄控制項, 項目狀態概觀"
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 樹狀目錄控制項目狀態概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 的每個項目都有目前狀態。  例如，項目可選取，停用，展開，依此類推。  在大部分的情況下，樹狀目錄控制項自動設定項目的狀態會反映使用者動作，例如項目選項。  不過，您可以使用 [GetItemState](../Topic/CTreeCtrl::GetItemState.md) 成員函式，您也可以設定項目的狀態使用 [SetItemState](../Topic/CTreeCtrl::SetItemState.md) 成員函式和擷取項目的目前狀態。  如需項目狀態的完整清單，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [樹狀檢視控制項常數](http://msdn.microsoft.com/library/windows/desktop/bb759985) 。  
  
 此項目的目前狀態是由 `nState` 參數指定。  樹狀目錄控制項可能會變更項目的狀態會反映自訂動作，例如選取項目或將焦點設定給項目。  此外，應用程式可能會變更項目的狀態、停用或隱藏項目或指定覆疊影像或狀態影像。  
  
 當您指定或變更項目的狀態時， `nStateMask` 參數會指定要設定哪些狀態位元和 `nState` 參數包含那些位元的新值。  例如，下列範例會變更父項目的目前狀態 \( `hParentItem`\) 指定在 `CTreeCtrl` 物件 \(`m_treeCtrl`\) 對 **TVIS\_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/CPP/tree-control-item-states-overview_1.cpp)]  
  
 變更狀態的另一個例子是設定項目的覆疊影像。  若要完成這項作業， `nStateMask` 必須包含 `TVIS_OVERLAYMASK` 值，或使用 [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) 巨集，因此， `nState` 必須包含移位的覆疊影像的以一起始的索引將八位元。  索引不能指派覆疊影像的 0。  必須已經覆疊影像到覆疊影像樹狀目錄控制項由 [CImageList::SetOverlayImage](../Topic/CImageList::SetOverlayImage.md) 函式的先前呼叫。  函式指定影像的以一起始的索引將;這是索引搭配 **INDEXTOOVERLAYMASK** 巨集。  樹狀目錄控制項有四個覆疊的影像。  
  
 要設定項目的狀態影像， `nStateMask` 必須包含 `TVIS_STATEIMAGEMASK` 值，或使用 [INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597) 巨集，因此， `nState` 必須包含移位的狀態影像的以一起始的索引是 12 位元。  索引可以設為 0 以指派沒有狀態影像。  如需覆疊和狀態影像的詳細資訊，請參閱 [樹狀目錄控制項影像清單](../mfc/tree-control-image-lists.md)。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)