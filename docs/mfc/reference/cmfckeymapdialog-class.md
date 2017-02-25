---
title: "CMFCKeyMapDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCKeyMapDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCKeyMapDialog class"
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCKeyMapDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCKeyMapDialog` 類別支援控制項與對應命令與鍵盤上的按鍵。  
  
## 語法  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](../Topic/CMFCKeyMapDialog::CMFCKeyMapDialog.md)|建構 `CMFCKeyMapDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCKeyMapDialog::DoModal](../Topic/CMFCKeyMapDialog::DoModal.md)|顯示鍵盤對應對話方塊。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCKeyMapDialog::FormatItem](../Topic/CMFCKeyMapDialog::FormatItem.md)|呼叫由架構建置描述金鑰對應的字串。  根據預設，字串包含命令名稱、快速鍵和快速鍵使用的描述。|  
|[CMFCKeyMapDialog::GetCommandKeys](../Topic/CMFCKeyMapDialog::GetCommandKeys.md)|擷取包含快速鍵清單與指定之命令的字串。|  
|[CMFCKeyMapDialog::OnInsertItem](../Topic/CMFCKeyMapDialog::OnInsertItem.md)|呼叫由架構，在新的項目插入支援鍵盤對應控制項的內部清單控制項之前。|  
|[CMFCKeyMapDialog::OnPrintHeader](../Topic/CMFCKeyMapDialog::OnPrintHeader.md)|呼叫由架構列印鍵盤對應資料行中的新網頁。|  
|[CMFCKeyMapDialog::OnPrintItem](../Topic/CMFCKeyMapDialog::OnPrintItem.md)|呼叫由架構列印鍵盤對應項目。|  
|[CMFCKeyMapDialog::OnSetColumns](../Topic/CMFCKeyMapDialog::OnSetColumns.md)|呼叫框架設定資料行的標題都支援鍵盤對應控制項的內部清單控制項。|  
|[CMFCKeyMapDialog::PrintKeyMap](../Topic/CMFCKeyMapDialog::PrintKeyMap.md)|呼叫框架，當使用者按一下 \[**列印**\] 按鈕。|  
|[CMFCKeyMapDialog::SetColumnsWidth](../Topic/CMFCKeyMapDialog::SetColumnsWidth.md)|呼叫框架設定資料行的寬度 \(以支援鍵盤對應控制項的內部清單控制項的。|  
  
## 備註  
 使用 `CMFCKeyMapDialog` 類別實作可調整大小的鍵盤對應對話方塊。    對話方塊中使用清單檢視控制項顯示鍵盤快速鍵和其相關聯的命令。  
  
 若要使用 `CMFCKeyMapDialog` 類別在應用程式中，則會將指標傳至主框架視窗當做參數傳遞至 `CMFCKeyMapDialog` 建構函式。    然後呼叫 `DoModal` 方法以啟動強制回應對話方塊。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## 需求  
 **標題:** afxkeymapdialog.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)