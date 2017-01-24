---
title: "CFindReplaceDialog Class | Microsoft Docs"
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
  - "CFindReplaceDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFindReplaceDialog class"
  - "Find/Replace dialog box"
  - "取代文字"
  - "取代文字, CFindReplaceDialog class"
  - "文字搜尋, CFindReplaceDialog class"
  - "文字搜尋, 取代文字"
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
caps.latest.revision: 25
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFindReplaceDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您實作標準字串尋找\/取代在應用程式中的對話方塊。  
  
## 語法  
  
```  
class CFindReplaceDialog : public CCommonDialog  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFindReplaceDialog::CFindReplaceDialog](../Topic/CFindReplaceDialog::CFindReplaceDialog.md)|呼叫這個建構函式 `CFindReplaceDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFindReplaceDialog::Create](../Topic/CFindReplaceDialog::Create.md)|建立和顯示 `CFindReplaceDialog` 對話方塊。|  
|[CFindReplaceDialog::FindNext](../Topic/CFindReplaceDialog::FindNext.md)|呼叫此函式以判斷使用者是否要尋找尋找下一個相符的字串。|  
|[CFindReplaceDialog::GetFindString](../Topic/CFindReplaceDialog::GetFindString.md)|呼叫此函式以取得目前尋找字串。|  
|[CFindReplaceDialog::GetNotifier](../Topic/CFindReplaceDialog::GetNotifier.md)|呼叫這個函式會擷取在您簽入的訊息處理常式的 **FINDREPLACE** 結構。|  
|[CFindReplaceDialog::GetReplaceString](../Topic/CFindReplaceDialog::GetReplaceString.md)|呼叫此函式以取得目前的取代字串。|  
|[CFindReplaceDialog::IsTerminating](../Topic/CFindReplaceDialog::IsTerminating.md)|呼叫此函式以判斷對話方塊已結束。|  
|[CFindReplaceDialog::MatchCase](../Topic/CFindReplaceDialog::MatchCase.md)|呼叫此函式以判斷使用者是否要完全符合搜尋字串的執行個體。|  
|[CFindReplaceDialog::MatchWholeWord](../Topic/CFindReplaceDialog::MatchWholeWord.md)|呼叫此函式以判斷使用者是否要全字拼寫須相符。|  
|[CFindReplaceDialog::ReplaceAll](../Topic/CFindReplaceDialog::ReplaceAll.md)|呼叫此函式以判斷使用者是否要字串的所有項目都會取代。|  
|[CFindReplaceDialog::ReplaceCurrent](../Topic/CFindReplaceDialog::ReplaceCurrent.md)|呼叫此函式以判斷使用者是否為目前的文字取代。|  
|[CFindReplaceDialog::SearchDown](../Topic/CFindReplaceDialog::SearchDown.md)|呼叫此函式以判斷使用者是否要向下搜尋執行。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFindReplaceDialog::m\_fr](../Topic/CFindReplaceDialog::m_fr.md)|用於的結構 `CFindReplaceDialog` 自訂物件。|  
  
## 備註  
 不同於其他 Windows 通用對話方塊，請在中，當它們在螢幕上時， `CFindReplaceDialog` 物件為非強制回應，允許使用者與其他視窗互動。  有兩種 `CFindReplaceDialog` 物件:尋找對話方塊和 \[尋找\/取代對話方塊。  雖然對話方塊允許使用者輸入搜尋，而搜尋\/取代字串，而不執行任何的搜尋或取代的函式。  您必須將這些加入應用程式。  
  
 若要建構 `CFindReplaceDialog` 物件，請使用沒有引數的提供的建構函式 \(\)。  由於這是一個非強制性回應對話方塊，請使用 **new** 運算子，而不是在堆疊上，請在堆積上的物件。  
  
 一旦 `CFindReplaceDialog` 物件建構時，您必須呼叫 [建立](../Topic/CFindReplaceDialog::Create.md) 成員函式建立和顯示對話方塊。  
  
 使用 [m\_fr](../Topic/CFindReplaceDialog::m_fr.md) 結構在呼叫之前 **建立**初始化對話方塊。  `m_fr` 結構是型別 [FINDREPLACE](http://msdn.microsoft.com/library/windows/desktop/ms646835)。  如需此結構的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 為了讓父視窗中要告知尋找\/取代要求，您可以處理這個登錄的訊息的框架視窗需要使用視窗 [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) 函式並使用 [ON\_REGISTERED\_MESSAGE](../Topic/ON_REGISTERED_MESSAGE.md) 訊息對應 \(Message Map 巨集。  
  
 您可以判斷使用者決定是否要結束時出現 `IsTerminating` 成員函式的對話方塊。  
  
 `CFindReplaceDialog` 仰賴隨附於 Windows 3.1 \(含\) 以後版本的 COMMDLG.DLL 檔案。  
  
 自訂對話方塊，請從 `CFindReplaceDialog`衍生類別，以提供自訂對話方塊範本並將訊息對應的處理會從擴充的控制項傳回的通知訊息。  應將所有未處理訊息加入至基底類別。  
  
 攔截函式不需要自訂。  
  
 如需使用 `CFindReplaceDialog`的資訊，請參閱 [通用對話方塊類別。](../../mfc/common-dialog-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFindReplaceDialog`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)