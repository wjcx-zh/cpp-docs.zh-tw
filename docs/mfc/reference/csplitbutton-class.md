---
title: "CSplitButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSplitButton class"
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSplitButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CSplitButton` 類別表示分割按鈕控制項。  分割按鈕控制項執行預設的行為，當使用者按一下按鈕時的主要部分，並且顯示下拉式功能表，當使用者按一下  按鈕的下拉箭號時。  
  
## 語法  
  
```  
class CSplitButton : public CButton  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSplitButton::CSplitButton](../Topic/CSplitButton::CSplitButton.md)|建構 `CSplitButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSplitButton::Create](../Topic/CSplitButton::Create.md)|建立具有指定樣式的分割按鈕控制項並將其附加至目前 `CSplitButton` 物件。|  
|[CSplitButton::SetDropDownMenu](../Topic/CSplitButton::SetDropDownMenu.md)|設定顯示的下拉式功能表，當使用者按一下目前分割按鈕控制項的下拉箭號時。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CSplitButton::OnDropDown](../Topic/CSplitButton::OnDropDown.md)|處理系統傳送的 `BCN_DROPDOWN` 通知，當使用者按一下目前分割按鈕控制項的下拉箭號時。|  
  
## 備註  
 `CSplitButton` 類別 [CButton](../../mfc/reference/cbutton-class.md) 從類別衍生。  分割按鈕控制項模式是 `BS_SPLITBUTTON`的按鈕控制項。  當使用者按一下下拉箭號時，它會顯示自訂功能表。  如需詳細資訊，請參閱 [Button 樣式](http://msdn.microsoft.com/library/windows/desktop/bb775951)的 `BS_SPLITBUTTON` 和 `BS_DEFSPLITBUTTON` 樣式。  
  
 下圖說明包含頁面巡覽區控制項和 \(1\) 分割按鈕控制項的對話方塊。  這個根 \(2\) 下拉箭號已經按一下 ，而  \(3\) 子功能表隨即顯示。  
  
 ![包含 Splitbutton 和 Pager 控制項的對話方塊。](../../mfc/reference/media/splitbutton_pager.png "SplitButton\_Pager")  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## 需求  
 **標題:** afxcmn.h  
  
 這個類別會在 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] \(含\) 以後版本支援。  
  
 這個類別還需要在 [Windows Vista 通用控制項的組建需求](../../mfc/build-requirements-for-windows-vista-common-controls.md)說明。  
  
## 請參閱  
 [CSplitButton Class](../../mfc/reference/csplitbutton-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)