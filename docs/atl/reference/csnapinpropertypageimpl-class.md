---
title: "CSnapInPropertyPageImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSnapInPropertyPageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSnapInPropertyPageImpl class"
  - "屬性頁, ATL"
  - "snap-ins"
  - "snap-ins, 屬性頁"
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSnapInPropertyPageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作嵌入式管理單元的屬性頁中物件的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
CSnapInPropertyPageImpl : public CDialogImplBase  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](../Topic/CSnapInPropertyPageImpl::CSnapInPropertyPageImpl.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSnapInPropertyPageImpl::CancelToClose](../Topic/CSnapInPropertyPageImpl::CancelToClose.md)|變更 \[**確定**\] 和 **取消** 按鈕的狀態。|  
|[CSnapInPropertyPageImpl::Create](../Topic/CSnapInPropertyPageImpl::Create.md)|表示初始化新建立的 `CSnapInPropertyPageImpl` 物件。|  
|[CSnapInPropertyPageImpl::OnApply](../Topic/CSnapInPropertyPageImpl::OnApply.md)|呼叫框架，當使用者按一下 \[**現在套用**\] 按鈕，當使用的精靈類型的屬性工作表時。|  
|[CSnapInPropertyPageImpl::OnHelp](../Topic/CSnapInPropertyPageImpl::OnHelp.md)|呼叫框架，當使用者按一下 **說明** 按鈕，當使用的精靈類型的屬性工作表時。|  
|[CSnapInPropertyPageImpl::OnKillActive](../Topic/CSnapInPropertyPageImpl::OnKillActive.md)|呼叫框架，在目前頁面不在使用中。|  
|[CSnapInPropertyPageImpl::OnQueryCancel](../Topic/CSnapInPropertyPageImpl::OnQueryCancel.md)|呼叫框架，當使用者按一下按鈕，並 **取消** ，取消之前發生。|  
|[CSnapInPropertyPageImpl::OnReset](../Topic/CSnapInPropertyPageImpl::OnReset.md)|呼叫框架，當使用者按一下 **重設** 按鈕，當使用的精靈類型的屬性工作表時。|  
|[CSnapInPropertyPageImpl::OnSetActive](../Topic/CSnapInPropertyPageImpl::OnSetActive.md)|呼叫框架，在目前頁面變成作用中。|  
|[CSnapInPropertyPageImpl::OnWizardBack](../Topic/CSnapInPropertyPageImpl::OnWizardBack.md)|呼叫框架，當使用者按一下**Back** 按鈕，當使用的精靈類型的屬性工作表時。|  
|[CSnapInPropertyPageImpl::OnWizardFinish](../Topic/CSnapInPropertyPageImpl::OnWizardFinish.md)|呼叫框架，當使用者按一下 **完成** 按鈕，當使用的精靈類型的屬性工作表時。|  
|[CSnapInPropertyPageImpl::OnWizardNext](../Topic/CSnapInPropertyPageImpl::OnWizardNext.md)|呼叫框架，當使用者按一下 `Next` 按鈕，當使用的精靈類型的屬性工作表時。|  
|[CSnapInPropertyPageImpl::QuerySiblings](../Topic/CSnapInPropertyPageImpl::QuerySiblings.md)|將目前訊息寫入屬性工作表的所有頁面。|  
|[CSnapInPropertyPageImpl::SetModified](../Topic/CSnapInPropertyPageImpl::SetModified.md)|啟用或停用 \[**現在套用**\] 按鈕上呼叫。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CSnapInPropertyPageImpl::m\_psp](../Topic/CSnapInPropertyPageImpl::m_psp.md)|`CSnapInPropertyPageImpl` 物件使用的視窗 **PROPSHEETPAGE** 結構。|  
  
## 備註  
 `CSnapInPropertyPageImpl` 為嵌入式管理單元屬性頁提供物件的基底實作。  嵌入式管理單元的屬性頁的基底實作功能時使用的數個不同介面並對應型別。  
  
## 繼承階層架構  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## 需求  
 **Header:** atlsnap.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)