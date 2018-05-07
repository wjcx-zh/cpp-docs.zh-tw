---
title: 使用影像清單與 Rebar 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f902cb24d5cd8525a99f58fc5feeac416138148
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-image-list-with-a-rebar-control"></a>搭配使用影像清單與 Rebar 控制項
除了其他方面，每個 Rebar 群組列還可以包含關聯影像清單中的影像。 下列程序詳述用於顯示 Rebar 群組列中影像的必要步驟。  
  
### <a name="to-display-images-in-a-rebar-band"></a>若要顯示 Rebar 群組列中影像  
  
1.  附加影像清單至 rebar 控制項物件呼叫[SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist)，將指標傳遞至現有的映像清單。  
  
2.  修改**REBARBANDINFO**結構以指派影像給 rebar 群組列：  
  
    -   設定**fMask**成員**RBBIM_IMAGE**，以包含其他旗標，視使用位元 OR 運算子。  
  
    -   設定 `iImage` 成員為顯示之影像的影像清單索引。  
  
3.  使用必要資訊初始化剩餘的資料成員，例如包含之子視窗的大小、文字和控制代碼。  
  
4.  插入 （與映像） 呼叫新頻外[CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband)，並傳遞**REBARBANDINFO**結構。  
  
 下列範例假設，具有兩個影像的現有影像清單物件已附加至 Rebar 控制項物件 (`m_wndReBar`)。 包含第一個影像的新 Rebar 群組列 (由 `rbi`所定義)，已新增對 `InsertBand` 的呼叫：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

