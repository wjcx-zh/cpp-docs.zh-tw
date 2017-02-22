---
title: "虛擬清單控制項 | Microsoft Docs"
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
  - "快取, 虛擬清單控制項目資料"
  - "清單控制項, 清單檢視"
  - "清單控制項, 虛擬"
  - "虛擬清單控制項"
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 虛擬清單控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虛擬清單控制項是具有 **LVS\_OWNERDATA** 的樣式清單檢視控制項。  此模式可讓控制項支援項目計數由 `DWORD` \(預設項目計數只延伸到 `int`\)。  不過，這個樣式提供最大的好處是能夠隨時只有資料項目的子集在記憶體中。  這可讓虛擬清單檢視控制項本身為與資訊大型資料庫的使用，存取特定資料的方法已經準備就緒。  
  
> [!NOTE]
>  除了提供 `CListCtrl`中的虛擬清單功能之外， MFC 也提供了 [CListView](../mfc/reference/clistview-class.md) 類別的相同功能。  
  
 您必須知道，在開發虛擬清單控制項時的一些相容性問題。  如需詳細資訊，請參閱相容性發行清單檢視控制項主題的部分以 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]為單位。  
  
## 處理 LVN\_GETDISPINFO 通知  
 虛擬清單控制項維護很少項目資訊。  除了項目選取範圍和焦點資訊，所有項目控制識別項的擁有者處理。  資訊由架構要求傳遞 **LVN\_GETDISPINFO** 通知訊息。  若要提供所要求的資訊，虛擬清單控制項的擁有人 \(或控制項\) 必須處理這個告知。  這可以輕鬆地使用屬性視窗 \(請參閱 [此函式之對應訊息](../mfc/reference/mapping-messages-to-functions.md)\)。  產生的程式碼應該看起來會像下列範例 \(其中 `CMyDialog` 擁有虛擬清單控制項物件，對話處理告知\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/CPP/virtual-list-controls_1.cpp)]  
  
 在 **LVN\_GETDISPINFO** 通知訊息的處理常式，您必須檢查何種資訊要求。  可能的值為：  
  
-   必須填入`LVIF_TEXT` `pszText` 成員。  
  
-   必須填入`LVIF_IMAGE` `iImage` 成員。  
  
-   必須填入**LVIF\_INDENT** 這個 *iIndent* 成員。  
  
-   必須填入`LVIF_PARAM` *lParam* 成員。\(子項目的不存在\)  
  
-   必須填入`LVIF_STATE` *狀態* 成員。  
  
 您應該就提供任何資訊要求回到上一個框架。  
  
 下列範例 \(從通知處理常式的主體清單控制項的物件\) 會提供項目的文字緩衝區和影像的資訊示範了可能的方法:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/CPP/virtual-list-controls_2.cpp)]  
  
## 快取和虛擬清單控制項  
 由於這種清單控制項供大型資料集使用，建議您快取要求項目資料改善擷取效能。  這個架構提供一個快取暗示的機制在最佳化快取的協助透過傳送 **LVN\_ODCACHEHINT** 通知訊息。  
  
 下列範例會更新其範圍快取傳遞至處理函式。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/CPP/virtual-list-controls_3.cpp)]  
  
 如需準備和維護快取的詳細資訊，請參閱清單檢視控制項主題的快取區管理服務以 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]為單位\)。  
  
## 尋找特定項目  
 **LVN\_ODFINDITEM** 通知訊息由虛擬清單控制項傳送特定清單控制項項目。  當清單檢視控制項接收快速鍵存取時會傳送通知訊息，或在收到 **LVM\_FINDITEM** 訊息時。  以 **LVFINDINFO** 結構的形式，搜尋資訊傳送，是 **NMLVFINDITEM** 結構的成員。  藉由覆寫您的清單控制項物件的 `OnChildNotify` 函式來處理這個訊息，以及內部處理常式的主體，檢查 **LVN\_ODFINDITEM** 訊息。  如果找到，請執行適當的動作。  
  
 您應該準備搜尋符合清單檢視控制項所提供的資訊的項目。  您應該傳回項目的索引，如果成功則為 \-1，如果找不到相符的項目。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)