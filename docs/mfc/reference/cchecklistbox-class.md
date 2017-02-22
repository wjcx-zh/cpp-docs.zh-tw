---
title: "CCheckListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCheckListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCheckListBox class"
  - "checklist boxes"
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CCheckListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供視窗清單方塊的功能。  
  
## 語法  
  
```  
  
class CCheckListBox : public CListBox  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCheckListBox::CCheckListBox](../Topic/CCheckListBox::CCheckListBox.md)|建構 `CCheckListBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCheckListBox::Create](../Topic/CCheckListBox::Create.md)|建立視窗清單方塊並將其附加至 `CCheckListBox` 物件。|  
|[CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md)|呼叫框架，其在主控描繪清單方塊的視覺外觀變更。|  
|[CCheckListBox::Enable](../Topic/CCheckListBox::Enable.md)|啟用或停用清單方塊項目。|  
|[CCheckListBox::GetCheck](../Topic/CCheckListBox::GetCheck.md)|取得項目的核取方塊的狀態。|  
|[CCheckListBox::GetCheckStyle](../Topic/CCheckListBox::GetCheckStyle.md)|取得控制項的核取方塊的樣式。|  
|[CCheckListBox::IsEnabled](../Topic/CCheckListBox::IsEnabled.md)|判斷項目是否已啟用。|  
|[CCheckListBox::MeasureItem](../Topic/CCheckListBox::MeasureItem.md)|呼叫框架，則會使用主控描繪模式來建立清單方塊。|  
|[CCheckListBox::OnGetCheckPosition](../Topic/CCheckListBox::OnGetCheckPosition.md)|呼叫框架取得項目的核取方塊的位置。|  
|[CCheckListBox::SetCheck](../Topic/CCheckListBox::SetCheck.md)|設定項目的核取方塊的狀態。|  
|[CCheckListBox::SetCheckStyle](../Topic/CCheckListBox::SetCheckStyle.md)|將控制項的核取方塊的樣式。|  
  
## 備註  
 「清單方塊」顯示項目清單，例如檔案名稱。  在  清單中的每個項目都有一個核取方塊旁邊使用者核取或清除。  
  
 `CCheckListBox` 僅供主控描繪控制項，因為清單的文字字串包含更多。  在最簡單，清單方塊會包含文字字串和核取方塊，不過，您完全不需要有文字。  例如，您可以在每個項目旁邊有核取方塊的小型點陣圖清單。  
  
 若要建立您自己的清單方塊，您必須從 `CCheckListBox`衍生您的類別。  若要衍生您的類別，提供衍生類別的建構函式，然後呼叫 **建立**。  
  
 如果您要處理的視窗清單方塊所傳送的通知訊息給它的父 [CDialog](../../mfc/reference/cdialog-class.md)\(通常是從衍生的類別\)，將訊息對應 \(Message Map 輸入和訊息處理常式成員函式來為每則訊息的父類別。  
  
 每個訊息對應 \(Message Map 輸入的格式如下:  
  
 **ON\_**告知**\(**`id`， `memberFxn`**\)**  
  
 其中 `id` 指定正在傳送之控制項的子視窗 ID 告知和 `memberFxn` 是您撰寫處理告知父代成員函式的名稱。  
  
 父的函式原型 \(Prototype\) 如下:  
  
 **afx\_msg** `void` `memberFxn` **\( \);**  
  
 只有明確地與 **CCheckListBox** 的訊息對應項目 \(，但是 [CListBox](../../mfc/reference/clistbox-class.md)也請參閱訊息對應 \(Message Map\) 輸入:  
  
-   **ON\_CLBN\_CHKCHANGE** 使用者已變更之項目的核取方塊的狀態。  
  
 如果您的清單方塊是預設清單方塊 \(使用預設大小\] 核取方塊的字串清單中每個的左側\)，您可以使用預設 [CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md) 繪製清單方塊。  否則，您必須覆寫 [CListBox::CompareItem](../Topic/CListBox::CompareItem.md) 函式和 [CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md) 和 [CCheckListBox::MeasureItem](../Topic/CCheckListBox::MeasureItem.md) 函式。  
  
 您可以建立一個清單方塊從對話方塊範本或直接在您的程式碼。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC TSTCON 範例](../../top/visual-cpp-samples.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)