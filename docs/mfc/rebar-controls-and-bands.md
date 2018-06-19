---
title: Rebar 控制項和群組列 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1fac5f83f19fab37604a14e239cf505891c737f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349847"
---
# <a name="rebar-controls-and-bands"></a>Rebar 控制項和群組列
Rebar 控制項的主要用途是做為子視窗、 通用對話方塊控制項、 功能表、 工具列和等等的容器。 這個內含項目會受到概念的 「 矩形 」。 每個 rebar 群組列可以包含移駐夾列、 點陣圖、 文字標籤和子視窗的任何組合。  
  
 類別`CReBarCtrl`具有許多成員函數，您可以用來擷取，並管理特定 rebar 群組列的資訊：  
  
-   [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount)擷取 rebar 控制項中目前的群組列的數目。  
  
-   [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo)初始化**REBARBANDINFO**結構指定的頻外的資訊。 沒有相對應[SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo)成員函式。  
  
-   [GetRect](../mfc/reference/crebarctrl-class.md#getrect)擷取指定的頻外框。  
  
-   [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount)擷取 rebar 控制項中的頻外資料列數目。  
  
-   [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex)擷取指定的群組列的索引。  
  
-   [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders)擷取的頻外框線。  
  
 除了操作，數個成員函式會提供可讓您在特定 rebar 群組列一起運作。  
  
 [InsertBand](../mfc/reference/crebarctrl-class.md#insertband)和[DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband)加入和移除 rebar 群組列。 [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband)和[MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband)會影響特定 rebar 群組列的目前大小。 [MoveBand](../mfc/reference/crebarctrl-class.md#moveband)變更特定 rebar 群組列的索引。 [ShowBand](../mfc/reference/crebarctrl-class.md#showband)顯示或隱藏使用者 rebar 群組列。  
  
 下列範例示範如何將工具列頻外 (`m_wndToolBar`) 至現有的 rebar 控制項 (`m_wndReBar`)。 初始化所描述的頻外`rbi`結構，然後再呼叫`InsertBand`成員函式：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

