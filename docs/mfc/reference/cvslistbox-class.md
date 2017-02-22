---
title: "CVSListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CVSListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CVSListBox class"
  - "CVSListBox::PreTranslateMessage method"
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CVSListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CVSListBox` 類別支援可編輯的清單控制項。  
  
## 語法  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CVSListBox::CVSListBox](../Topic/CVSListBox::CVSListBox.md)|建構 `CVSListBox` 物件。|  
|`CVSListBox::~CVSListBox`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CVSListBox::AddItem](../Topic/CVSListBox::AddItem.md)|將字串加入至清單控制項。  \(覆寫 `CVSListBoxBase::AddItem`\)。|  
|[CVSListBox::EditItem](../Topic/CVSListBox::EditItem.md)|開始在清單控制項項目文字的編輯作業。  \(覆寫 `CVSListBoxBase::EditItem`\)。|  
|[CVSListBox::GetCount](../Topic/CVSListBox::GetCount.md)|擷取字串數目可編輯的清單控制項的。  \(覆寫 `CVSListBoxBase::GetCount`\)。|  
|[CVSListBox::GetItemData](../Topic/CVSListBox::GetItemData.md)|擷取與一個可編輯的清單控制項項目的特定應用程式的 32 位元值。  \(覆寫 `CVSListBoxBase::GetItemData`\)。|  
|[CVSListBox::GetItemText](../Topic/CVSListBox::GetItemText.md)|擷取可編輯的清單控制項項目的文字。  \(覆寫 `CVSListBoxBase::GetItemText`\)。|  
|[CVSListBox::GetSelItem](../Topic/CVSListBox::GetSelItem.md)|擷取目前選取之項目的以零起始的索引中可編輯的清單控制項的。  \(覆寫 `CVSListBoxBase::GetSelItem`\)。|  
|`CVSListBox::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  如需詳細資訊和方法語法的詳細資訊，請參閱 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。  \(覆寫 `CVSListBoxBase::PreTranslateMessage`\)。|  
|[CVSListBox::RemoveItem](../Topic/CVSListBox::RemoveItem.md)|從一個可編輯的清單控制項中移除項目。  \(覆寫 `CVSListBoxBase::RemoveItem`\)。|  
|[CVSListBox::SelectItem](../Topic/CVSListBox::SelectItem.md)|選項可編輯的清單控制項的字串。  \(覆寫 `CVSListBoxBase::SelectItem`\)。|  
|[CVSListBox::SetItemData](../Topic/CVSListBox::SetItemData.md)|關聯應用程式特定的 32 位元值的可編輯的清單控制項項目。  \(覆寫 `CVSListBoxBase::SetItemData`\)。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CVSListBox::GetListHwnd](../Topic/CVSListBox::GetListHwnd.md)|將控制代碼傳回給目前內嵌清單檢視控制項。|  
  
## 備註  
 `CVSListBox` 類別提供一組可讓使用者建立，修改，刪除或重新排列在清單控制項中項目的編輯按鈕。  
  
 以下是可編輯的清單控制項的圖片。  第二個清單項目，名為「Item2」，以供編輯的選項。  
  
 ![CVSListBox 控制項](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 如果您使用資源編輯器將可編輯的清單控制項，請注意編輯器的 \[**工具箱**\] 窗格不提供預先定義的可編輯的清單控制項。  相反地，請將靜態控制項 \(例如控制項 \[**群組方塊**\] 。  架構會使用靜態控制項做為預留位置指定可編輯的清單控制項的大小和位置。  
  
 若要使用可編輯的清單控制項在對話方塊中的範本，請在您的對話方塊類別的一 `CVSListBox` 變數。  若要支援資料交換在變數和控制項之間，定義在  對話方塊中的 `DoDataExchange` 方法的 `DDX_Control` 巨集輸入。  根據預設，可編輯的清單控制項建立，而不需要編輯按鈕。  使用繼承的 [CVSListBoxBase::SetStandardButtons](http://msdn.microsoft.com/zh-tw/129e530f-97e9-42eb-b128-371c2a5686ba) 方法啟用編輯按鈕。  
  
 如需詳細資訊，請參閱範例目錄、 `New Controls` 範例， Page3.cpp 和 Page3.h 檔案。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## 需求  
 **標題:** afxvslistbox.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)