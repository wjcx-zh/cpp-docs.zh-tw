---
title: "CComboBoxEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComboBoxEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBoxEx class"
  - "下拉式方塊 [C++], CComboBoxEx class"
  - "common controls [C++], extended combo boxes"
  - "extended combo boxes, CComboBoxEx class"
  - "Internet Explorer 4.0 common controls"
  - "Windows common controls [C++], extended combo boxes"
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComboBoxEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

藉由提供支援放大下拉式方塊控制項影像清單的。  
  
## 語法  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComboBoxEx::CComboBoxEx](../Topic/CComboBoxEx::CComboBoxEx.md)|建構 `CComboBoxEx` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComboBoxEx::Create](../Topic/CComboBoxEx::Create.md)|建立下拉式方塊並將其附加至 `CComboBoxEx` 物件。|  
|[CComboBoxEx::CreateEx](../Topic/CComboBoxEx::CreateEx.md)|建立擁有指定之視窗的延伸樣式的下拉式方塊並將其附加至 **ComboBoxEx** 物件。|  
|[CComboBoxEx::DeleteItem](../Topic/CComboBoxEx::DeleteItem.md)|從 **ComboBoxEx** 控制項中移除項目。|  
|[CComboBoxEx::GetComboBoxCtrl](../Topic/CComboBoxEx::GetComboBoxCtrl.md)|擷取指標子下拉式方塊控制項。|  
|[CComboBoxEx::GetEditCtrl](../Topic/CComboBoxEx::GetEditCtrl.md)|擷取控制代碼 **ComboBoxEx** 控制項的編輯控制項部分。|  
|[CComboBoxEx::GetExtendedStyle](../Topic/CComboBoxEx::GetExtendedStyle.md)|擷取之前為 **ComboBoxEx** 控制正在使用中的延伸樣式。|  
|[CComboBoxEx::GetImageList](../Topic/CComboBoxEx::GetImageList.md)|擷取指標至影像清單的 **ComboBoxEx** 指派給控制項。|  
|[CComboBoxEx::GetItem](../Topic/CComboBoxEx::GetItem.md)|擷取指定之 **ComboBoxEx** 項目資訊。|  
|[CComboBoxEx::HasEditChanged](../Topic/CComboBoxEx::HasEditChanged.md)|判斷使用者是否已輸入變更 **ComboBoxEx** 編輯控制項的內容。|  
|[CComboBoxEx::InsertItem](../Topic/CComboBoxEx::InsertItem.md)|在 **ComboBoxEx** 控制項插入新的項目。|  
|[CComboBoxEx::SetExtendedStyle](../Topic/CComboBoxEx::SetExtendedStyle.md)|在 **ComboBoxEx** 控制項中集合的延伸樣式。|  
|[CComboBoxEx::SetImageList](../Topic/CComboBoxEx::SetImageList.md)|設定 **ComboBoxEx** 控制項中的影像清單。|  
|[CComboBoxEx::SetItem](../Topic/CComboBoxEx::SetItem.md)|設定項目的屬性 \(Attribute\)。 **ComboBoxEx** 控制項。|  
|[CComboBoxEx::SetWindowTheme](../Topic/CComboBoxEx::SetWindowTheme.md)|設定展開的下拉式方塊控制項的視覺化樣式。|  
  
## 備註  
 您可以使用建立下拉式方塊控制項的 `CComboBoxEx` ，您不再需要實作自己的影像繪製程式碼。  相反地，會使用從影像 `CComboBoxEx` 存取影像清單。  
  
## 影像清單支援  
 在標準下拉式方塊，下拉式方塊的擁有人負責繪製影像會透過建立下拉式方塊為主控描繪控制項。  當您使用 `CComboBoxEx`時，則不需要設定的繪製樣式 **CBS\_OWNERDRAWFIXED** 和 **CBS\_HASSTRINGS** ，因為它們是隱含的。  否則，您必須撰寫程式碼來執行繪製作業。  `CComboBoxEx` 控制項支援每一個項目的三個影像:單一選取的狀態，一個未選取的狀態、以及一個覆疊影像的。  
  
## 樣式  
 `CComboBoxEx` 支援樣式 **CBS\_SIMPLE**、 **CBS\_DROPDOWN**、 **CBS\_DROPDOWNLIST**和 **WS\_CHILD**。  透過的其他模式，在建立視窗時由控制項會忽略。  在建立視窗之後，您就可以呼叫 `CComboBoxEx` 成員函式提供其他下拉式方塊樣式 [SetExtendedStyle](../Topic/CComboBoxEx::SetExtendedStyle.md)。  這些樣式，您可以:  
  
-   設定  清單中的字串搜尋區分大小寫。  
  
-   建立使用斜線的下拉式方塊控制項 \(「\/「\)，反斜線 \(「\\ 「\) 和句號 \(「。」\) 字元在字組分隔符號。  使用鍵盤快速鍵 CTRL\+ 向上鍵，這可讓使用者從 Word 跳至文字。  
  
-   將下拉式方塊控制項中顯示或不顯示影像。  如果影像沒有顯示，下拉式方塊可以移除以容納影像的文字縮排。  
  
-   建立窄下拉式方塊控制項，包括讓它，所以它的包含其裁剪更廣的下拉式方塊。  
  
 這些樣式旗標進一步在 [使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)說明。  
  
## 項目會保留和回呼內項目的屬性。  
 項目資訊，例如項目和影像的索引，表示縮排值和文字字串，在 Win32 結構 [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746)儲存 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，如中所述。  結構也包含對應回呼旗標的成員。  
  
 如需深入的概念，討論，請參閱 [使用 CComboBoxEx](../../mfc/using-ccomboboxex.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 MFCIE](../../top/visual-cpp-samples.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)