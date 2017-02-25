---
title: "CMFCMaskedEdit Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCMaskedEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMaskedEdit class"
  - "CMFCMaskedEdit constructor"
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCMaskedEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCMaskedEdit` 類別支援一 Masked Edit 控制項、驗證使用者輸入，針對遮罩並根據範本顯示驗證的結果。  
  
## 語法  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|預設建構函式。|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCMaskedEdit::DisableMask](../Topic/CMFCMaskedEdit::DisableMask.md)|驗證使用者輸入的停用。|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](../Topic/CMFCMaskedEdit::EnableGetMaskedCharsOnly.md)|指定 `GetWindowText` 方法是否只擷取遮罩字元。|  
|[CMFCMaskedEdit::EnableMask](../Topic/CMFCMaskedEdit::EnableMask.md)|初始化 Masked Edit 控制項。|  
|[CMFCMaskedEdit::EnableSelectByGroup](../Topic/CMFCMaskedEdit::EnableSelectByGroup.md)|指定 Masked Edit 控制項是否選取使用者輸入的特定群組，或所有使用者輸入。|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](../Topic/CMFCMaskedEdit::EnableSetMaskedCharsOnly.md)|指定文字是否已經驗證只會遮罩字元，或針對整體遮罩。|  
|`CMFCMaskedEdit::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCMaskedEdit::GetWindowText](../Topic/CMFCMaskedEdit::GetWindowText.md)|擷取驗證從 Masked Edit 控制項的文字。|  
|[CMFCMaskedEdit::SetValidChars](../Topic/CMFCMaskedEdit::SetValidChars.md)|指定使用者可以輸入有效字元的字串。|  
|[CMFCMaskedEdit::SetWindowText](../Topic/CMFCMaskedEdit::SetWindowText.md)|顯示在 Masked Edit 控制項的提示。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCMaskedEdit::IsMaskedChar](../Topic/CMFCMaskedEdit::IsMaskedChar.md)|呼叫由架構驗證指定的字元在與對應的遮罩字元。|  
  
## 備註  
 執行下列步驟 `CMFCMaskedEdit` 使用控制項在應用程式:  
  
 1.  將一 `CMFCMaskedEdit` 物件插入您的視窗類別。  
  
 2.  呼叫方法 [CMFCMaskedEdit::EnableMask](../Topic/CMFCMaskedEdit::EnableMask.md) 指定遮罩。  
  
 3.  呼叫方法 [CMFCMaskedEdit::SetValidChars](../Topic/CMFCMaskedEdit::SetValidChars.md) 指定有效的字元清單。  
  
 4.  呼叫方法以 [CMFCMaskedEdit::SetWindowText](../Topic/CMFCMaskedEdit::SetWindowText.md) Masked Edit 控制項指定預設文字。  
  
 5.  呼叫方法 [CMFCMaskedEdit::GetWindowText](../Topic/CMFCMaskedEdit::GetWindowText.md) 擷取驗證的文字。  
  
 如果您未呼叫一或多個方法初始化遮罩、有效字元和預設文字， Masked Edit 控制項的行為就像標準的編輯控制項的行為。  
  
## 範例  
 下列範例會示範如何設定遮罩 \(例如電話號碼\) 使用方法建立 `EnableMask` Masked Edit 控制項、 `SetValidChars` 方法指定使用者可以輸入有效字元的字串和 `SetWindowText` 方法的遮罩可以顯示 Masked Edit 控制項的提示。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#11](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#11)]  
[!CODE [NVC_MFC_NewControls#12](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#12)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## 需求  
 **標題:** afxmaskededit.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)