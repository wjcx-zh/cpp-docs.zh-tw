---
title: "建立索引標籤控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TCS_EX_REGISTERDROP"
  - "TCS_EX_FLATSEPARATORS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabCtrl 類別, 建立"
  - "索引標籤控制項, 建立"
  - "TCS_EX_FLATSEPARATORS 延伸樣式"
  - "TCS_EX_REGISTERDROP 延伸樣式"
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立索引標籤控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

索引標籤控制項的建立方式，取決於您是在對話方塊中使用控制項或在 nondialog 視窗建立它。  
  
### 若要直接在對話方塊使用 CTabCtrl  
  
1.  在對話方塊編輯器中，將索引標籤控制項加入至對話方塊樣板資源。  指定它的控制項 ID.  
  
2.  使用 [加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md) 將型別 [CTabCtrl](../mfc/reference/ctabctrl-class.md) 的成員變數加入至控制項屬性。  您可以使用這個成員呼叫 `CTabCtrl` 成員函式。  
  
3.  將對話方塊類別中的處理函式對應至需要處理的任何索引標籤控制項通知訊息。  如需詳細資訊，請參閱[將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
4.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 中，設定 `CTabCtrl` 的樣式。  
  
### 若要在 nondialog 視窗使用 CTabCtrl  
  
1.  在檢視或視窗類別定義控制項。  
  
2.  呼叫控制項的 [建立](../Topic/CTabCtrl::Create.md) 成員函式 \(可能在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 中\)，並且盡可能的與父視窗的 [OnCreate](../Topic/CWnd::OnCreate.md) 處理常式函式一樣早 \(如果您是繼承控制項\) 。  設定控制項的樣式。  
  
 在 `CTabCtrl` 物件建立之後，您可以設定或清除下列延伸樣式：  
  
-   **TCS\_EX\_FLATSEPARATORS** 索引標籤控制項會在索引標籤項目之間繪製分隔符號。  這個延伸樣式只會影響擁有 **TCS\_BUTTONS** 和 **TCS\_FLATBUTTONS** 樣式的索引標籤控制項。  根據預設，以 **TCS\_FLATBUTTONS** 樣式建立的索引標籤控制項會設定此延伸樣式。  
  
-   **TCS\_EX\_REGISTERDROP** 將物件拖曳索引標籤項目至控制項時，索引標籤控制項產生 **TCN\_GETOBJECT** 通知訊息要求置放目標物件。  
  
    > [!NOTE]
    >  若要接收 **TCN\_GETOBJECT** 通知，您必須呼叫 [AfxOleInit](../Topic/AfxOleInit.md) 初始化 OLE 程式庫。  
  
 在建立控制項之後，這些樣式可以分別呼叫 [GetExtendedStyle](../Topic/CTabCtrl::GetExtendedStyle.md) 和 [SetExtendedStyle](../Topic/CTabCtrl::SetExtendedStyle.md) 成員函式，進行擷取和設定。  
  
 例如，將下列程式碼設定 **TCS\_EX\_FLATSEPARATORS** 樣式：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/CPP/creating-the-tab-control_1.cpp)]  
  
 以下列程式碼清除 `CTabCtrl` 物件的 **TCS\_EX\_FLATSEPARATORS** 樣式：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/CPP/creating-the-tab-control_2.cpp)]  
  
 這會移除顯示在您的 `CTabCtrl` 物件之間的按鈕分隔符號。  
  
## 請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)