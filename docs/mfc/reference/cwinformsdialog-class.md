---
title: "CWinFormsDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsDialog class"
  - "MFC [C++], Windows Form 支援"
  - "Windows Form [C++], MFC 支援"
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CWinFormsDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 Windows Form 使用者控制項裝載為 MFC 對話方塊類別的包裝函式。  
  
## 語法  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
   public CDialog  
```  
  
#### 參數  
 `TManagedControl`  
 在 MFC 應用程式中顯示的 .NET Framework 使用者控制項。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsDialog::CWinFormsDialog](../Topic/CWinFormsDialog::CWinFormsDialog.md)|建構 `CWinFormsDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinFormsDialog::GetControl](../Topic/CWinFormsDialog::GetControl.md)|擷取對 Windows Form 使用者控制項的參考。|  
|[CWinFormsDialog::GetControlHandle](../Topic/CWinFormsDialog::GetControlHandle.md)|擷取視窗控制代碼的 Windows Form 使用者控制項。|  
|[CWinFormsDialog::OnInitDialog](../Topic/CWinFormsDialog::OnInitDialog.md)|藉由建立和裝載之 Windows Form 使用者控制項初始化 MFC 對話方塊。|  
  
### 公用運算子  
  
|名稱||  
|--------|-|  
|[CWinFormsDialog::operator \-\>](../Topic/CWinFormsDialog::operator%20-%3E.md)|在取代運算式中 [CWinFormsDialog::GetControl](../Topic/CWinFormsDialog::GetControl.md) 。|  
|[CWinFormsDialog::operator TManagedControl^](../Topic/CWinFormsDialog::operator%20TManagedControl%5E.md)|做為 Windows Form 使用者控制項的參考轉換為型別。|  
  
## 備註  
 `CWinFormsDialog` 是 MFC 對話方塊的類別 \([CDialog](../../mfc/reference/cdialog-class.md)\) 包裝函式裝載 Windows Form 使用者控制項 \(<xref:System.Windows.Forms.UserControl>\)。  這可讓 .NET Framework 控制項顯示在強制回應或非強制回應的 MFC 對話方塊中的。  
  
 如需使用 Windows Form 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md) 和 [將 Windows Form 使用者控制項裝載成 MFC 對話方塊](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。  
  
## 需求  
 **標題:** afxwinforms.h  
  
## 請參閱  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)