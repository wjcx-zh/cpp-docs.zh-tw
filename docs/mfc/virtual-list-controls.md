---
title: 虛擬清單控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4891a4ccacf57dc43788bfa2a82decbe32961fb
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952823"
---
# <a name="virtual-list-controls"></a>虛擬清單控制項
虛擬清單控制項是具有 LVS_OWNERDATA 樣式清單檢視控制項。 這個樣式可讓控制項最多支援項目計數**DWORD** (預設項目計數只會延伸到**int**)。 不過，此樣式所提供的最大優點是能夠一次只能有在記憶體中的資料項目的子集。 這可讓虛擬清單檢視控制項本身的資訊，大型資料庫搭配使用特定的方法，存取資料的已備妥。  
  
> [!NOTE]
>  除了提供中的虛擬清單功能`CListCtrl`，MFC 也提供在相同的功能[CListView](../mfc/reference/clistview-class.md)類別。  
  
 有一些相容性問題，您應該注意的開發虛擬清單控制項時。 如需詳細資訊，請參閱清單檢視控制項中的主題 Windows SDK 的相容性問題 > 一節。  
  
## <a name="handling-the-lvngetdispinfo-notification"></a>處理 LVN_GETDISPINFO 通知  
 虛擬清單控制項維護非常少的項目資訊。 除了項目選取範圍和焦點資訊中，所有項目資訊是控制項的擁有者所管理。 由架構透過 LVN_GETDISPINFO 通知訊息被要求之資訊。 若要提供所要求的資訊，虛擬清單控制項 （或在控制項本身） 的擁有者必須處理這個通知。 這可以輕鬆地完成使用 [屬性] 視窗 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。 產生的程式碼看起來應該類似下列範例 (其中`CMyDialog`擁有虛擬清單控制項物件和對話方塊正在處理通知):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]  
  
 在 LVN_GETDISPINFO 通知訊息的處理常式，您必須檢查所要求的資訊類型。 可能值為：  
  
-   `LVIF_TEXT` *PszText*成員必須填入。  
  
-   `LVIF_IMAGE` *IImage*成員必須填入。  
  
-   `LVIF_INDENT` *IIndent*成員必須填入。  
  
-   `LVIF_PARAM` *LParam*成員必須填入。 （不存在的子項目。）  
  
-   `LVIF_STATE` *狀態*成員必須填入。  
  
 然後，您應該提供給架構要求的資訊。  
  
 （取自清單控制項物件的通知處理常式的主體） 的下列範例會示範其中一種方法，藉由提供文字緩衝區和映像項目的資訊：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]  
  
## <a name="caching-and-virtual-list-controls"></a>快取和虛擬清單控制項  
 因為這種類型的清單控制項要用於大型資料集，因此建議您快取要求的項目資料來改善擷取效能。 架構會提供快取提示的機制，以協助最佳化快取透過傳送 LVN_ODCACHEHINT 通知訊息。  
  
 下列範例會更新快取傳遞至處理常式函式的範圍。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]  
  
 如需有關準備和維護快取的詳細資訊，請參閱清單檢視控制項中的主題 Windows SDK 中的快取管理 > 一節。  
  
## <a name="finding-specific-items"></a>尋找特定項目  
 要尋找需要的特定清單控制項項目時，會傳送虛擬清單控制項 LVN_ODFINDITEM 通知訊息。 當清單檢視控制項接收快速金鑰的存取，或在收到 LVM_FINDITEM 訊息時，會傳送通知訊息。 搜尋資訊的形式傳送**LVFINDINFO**結構，也就是成員的**NMLVFINDITEM**結構。 處理此訊息透過覆寫`OnChildNotify`函式清單的控制項物件，並處理常式的本文內檢查 LVN_ODFINDITEM 訊息。 如果找到，請執行適當的動作。  
  
 您應該備妥要搜尋的項目符合指定的清單檢視控制項的資訊。 如果找到相符的項目，您應該傳回的項目，如果成功，則為-1 的索引。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

