---
title: "CDataExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDataExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataExchange class"
  - "DDV (dialog data validation)"
  - "DDV (dialog data validation), custom DDV routines"
  - "DDX (對話資料交換)"
  - "DDX (對話資料交換), between dialog and CDialog"
  - "DDX (對話資料交換), custom DDX routines"
  - "DDX (對話資料交換), direction of exchange"
  - "DDX/DDV"
  - "DDX/DDV, CDataExchange class"
  - "DDX/DDV, Technical Note 26"
  - "exchanging data between dialogs and CDialogs"
  - "m_bSaveAndValidate"
  - "驗證資料, dialog box data entry"
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CDataExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援的對話資料交換 \(Dialog Data Exchange，DDX\)，且對話資料驗證 Microsoft Foundation \(DDV\) 使用的常式分類。  
  
## 語法  
  
```  
class CDataExchange  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDataExchange::CDataExchange](../Topic/CDataExchange::CDataExchange.md)|建構 `CDataExchange` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDataExchange::Fail](../Topic/CDataExchange::Fail.md)|呼叫，驗證會失敗。  重設焦點至前一個控制項會擲回例外狀況。|  
|[CDataExchange::PrepareCtrl](../Topic/CDataExchange::PrepareCtrl.md)|指定的控制項進行資料交換或驗證的準備工作。  nonedit 控制項的用法。|  
|[CDataExchange::PrepareEditCtrl](../Topic/CDataExchange::PrepareEditCtrl.md)|指定的編輯控制項進行資料交換或驗證的準備工作。|  
|[CDataExchange::PrepareOleCtrl](../Topic/CDataExchange::PrepareOleCtrl.md)|指定的 OLE 控制項進行資料交換或驗證的準備工作。  nonedit 控制項的用法。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDataExchange::m\_bSaveAndValidate](../Topic/CDataExchange::m_bSaveAndValidate.md)|提供有關 DDX 和 DDV 方向旗標。|  
|[CDataExchange::m\_pDlgWnd](../Topic/CDataExchange::m_pDlgWnd.md)|對話方塊或視窗中進行資料交換出現的位置。|  
  
## 備註  
 `CDataExchange` 不具有基底類別。  
  
 請使用這個類別中，如果您為自訂資料型別或控制項撰寫資料交換常式，或者，如果您正在撰寫自己的資料驗證常式。  如需撰寫自己的 DDX 和 DDV 常式的詳細資訊，請參閱 [Technical Note 26](../../mfc/tn026-ddx-and-ddv-routines.md)。  如需有關 DDX 和 DDV 概觀，請參閱 [對話資料交換和驗證。](../../mfc/dialog-data-exchange-and-validation.md) 和 [對話方塊](../../mfc/dialog-boxes.md)。  
  
 `CDataExchange` 物件為 DDX 和 DDV 提供所需的內容資訊時發生。  當 DDX 可用來從資料成員時，填入對話方塊控制項的初始值旗標 `m_bSaveAndValidate` 是 **否** 。  旗標 `m_bSaveAndValidate` 是 **是** ，當 DDX 會用來設定對話方塊控制項的目前值輸入資料成員，不過，或當 DDV 用來驗證資料值時。  如果 DDV 驗證失敗， DDV 程序會顯示說明輸入錯誤的訊息方塊。  DDV 程序會呼叫 **失敗** 重設焦點設定為違規的控制項會擲回例外狀況會停止驗證程序。  
  
## 繼承階層架構  
 `CDataExchange`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC 範例 VIEWEX](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)   
 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)