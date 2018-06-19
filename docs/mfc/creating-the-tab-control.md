---
title: 建立索引標籤控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
dev_langs:
- C++
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3945d441130d723bbda3d137f2adae637d56c2b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344087"
---
# <a name="creating-the-tab-control"></a>建立索引標籤控制項
建立索引標籤控制項的方式取決於您是使用控制項在對話方塊中還是非對話方塊視窗中建立。  
  
### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CTabCtrl  
  
1.  在對話方塊編輯器中，將索引標籤控制項加入至對話方塊範本資源。 指定其控制項 ID.  
  
2.  使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)新增類型的成員變數[CTabCtrl](../mfc/reference/ctabctrl-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CTabCtrl` 成員函式。  
  
3.  對應處理常式函式，您需要處理的任何索引標籤控制項通知訊息的對話方塊類別中。 如需詳細資訊，請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
4.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定的樣式`CTabCtrl`。  
  
### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>若要在非對話方塊視窗中使用 CTabCtrl  
  
1.  在檢視或視窗類別中定義控制項。  
  
2.  呼叫控制項的[建立](../mfc/reference/ctabctrl-class.md#create)成員函式，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，方式與父視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。  
  
 之後`CTabCtrl`已建立物件，您可以設定或清除下列擴充樣式：  
  
-   **TCS_EX_FLATSEPARATORS**索引標籤控制項時，會在索引標籤項目之間繪製分隔符號。 這會擴充樣式，只會影響索引標籤控制項具有**TCS_BUTTONS**和**TCS_FLATBUTTONS**樣式。 根據預設，建立與此索引標籤控制項**TCS_FLATBUTTONS**樣式設定這個項目延伸樣式。  
  
-   **TCS_EX_REGISTERDROP**  索引標籤控制項產生**TCN_GETOBJECT**通知訊息以要求置放目標物件時將物件拖曳在控制項中的索引標籤項目。  
  
    > [!NOTE]
    >  若要接收**TCN_GETOBJECT**通知，您必須先初始化 OLE 程式庫呼叫[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。  
  
 擷取也已經建立控制項，個別呼叫之後設定這些樣式[GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle)和[SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle)成員函式。  
  
 例如，設定**TCS_EX_FLATSEPARATORS**樣式與下列程式碼：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]  
  
 清除**TCS_EX_FLATSEPARATORS**樣式從`CTabCtrl`與下列程式碼的物件：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]  
  
 這將會移除顯示的按鈕之間的分隔符號您`CTabCtrl`物件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)

