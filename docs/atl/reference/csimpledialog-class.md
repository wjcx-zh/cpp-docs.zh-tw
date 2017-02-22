---
title: "CSimpleDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CSimpleDialog"
  - "CSimpleDialgo"
  - "CSimpleDialog"
  - "ATL.CSimpleDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleDialog class"
  - "CSimpleDialog class, modal dialog boxes in ATL"
  - "對話方塊, 強制回應"
  - "強制回應對話方塊, ATL"
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSimpleDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作基本的強制回應對話方塊。  
  
## 語法  
  
```  
  
      template <  
   WORD t_wDlgTemplateID,  
   BOOL t_bCenter = TRUE  
>  
class CSimpleDialog :  
   public CDialogImplBase  
```  
  
#### 參數  
 *t\_wDlgTemplateID*  
  
 對話方塊樣板資源中的資源 ID。  
  
 *t\_bCenter*  
 **是** ，如果對話方塊物件要中央主控視窗，否則 **否**。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleDialog::DoModal](../Topic/CSimpleDialog::DoModal.md)|建立強制回應對話方塊。|  
  
## 備註  
 實作的基本功能的強制回應對話方塊。  `CSimpleDialog` 僅適用 Windows 通用控制項的支援。  若要建立和顯示強制回應對話方塊，建立這個類別的執行個體，可提供現有資源樣板名稱對話方塊。  對話方塊關閉物件，當使用者按一下含有預先定義值的所有控制項 \(例如或\) IDOK IDCANCEL。  
  
 `CSimpleDialog` 允許您建立只有強制回應對話方塊。  `CSimpleDialog` 提供對話方塊程序，使用預設的訊息對應會用來導向訊息給適當的處理常式。  
  
 請參閱 [實作對話方塊](../../atl/implementing-a-dialog-box.md) 以取得詳細資訊。  
  
## 繼承階層架構  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)