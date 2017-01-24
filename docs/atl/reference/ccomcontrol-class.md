---
title: "CComControl Class | Microsoft Docs"
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
  - "CComControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ambient properties"
  - "CComControl class"
  - "CComControlBase class, CComControl class"
  - "control flags"
  - "控制項 [ATL], control helper functions"
  - "控制項 [ATL], 屬性"
  - "內建屬性, ATL"
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立和管理 ATL 控制項的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class WinBase= CWindowImpl< T>   
>  
class ATL_NO_VTABLE CComControl :  
public CComControlBase, public WinBase;  
```  
  
#### 參數  
 `T`  
 實作控制項的類別。  
  
 *WinBase*  
 基底類別實作 Windowing 函式。  為 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)的預設值。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComControl::CComControl](../Topic/CComControl::CComControl.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComControl::ControlQueryInterface](../Topic/CComControl::ControlQueryInterface.md)|擷取指標所要求的介面。|  
|[CComControl::CreateControlWindow](../Topic/CComControl::CreateControlWindow.md)|建立控制項的視窗。|  
|[CComControl::FireOnChanged](../Topic/CComControl::FireOnChanged.md)|通知接收控制項容器的屬性已變更。|  
|[CComControl::FireOnRequestEdit](../Topic/CComControl::FireOnRequestEdit.md)|通知接收控制項容器的屬性將會變更，而且物件是存取接收如何繼續執行。|  
|[CComControl::MessageBox](../Topic/CComControl::MessageBox.md)|呼叫這個方法，以建立顯示和管理訊息方塊。|  
  
## 備註  
 `CComControl` 是一組控制項有用的 Helper 函式和基本資料成員 ATL 控制項。  使用 ATL 控制項精靈，當您建立標準控制項或 DHTML 控制項，從  `CComControl`會自動衍生您的類別。  `CComControl` 從 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)衍生其大部分方法。  
  
 如需建立控制項的詳細資訊，請參閱 [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  如需 ATL 專案精靈的詳細資訊，請參閱本文 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。  
  
 如需 `CComControl` 方法和資料成員的示範，請參閱 [CIRC](../../top/visual-cpp-samples.md) 範例。  
  
## 繼承階層架構  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComControlBase Class](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl Class](../../atl/reference/ccomcompositecontrol-class.md)