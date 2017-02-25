---
title: "CComCompositeControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComCompositeControl"
  - "ATL::CComCompositeControl"
  - "ATL.CComCompositeControl<T>"
  - "ATL.CComCompositeControl"
  - "ATL::CComCompositeControl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCompositeControl class"
  - "複合控制項, CComCompositeControl class"
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComCompositeControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供要求的方法實作複合控制項。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T   
>  
class CComCompositeControl :  
public CComControl< T, CAxDialogImpl< T > >  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從介面任何其他您想要為複合控制項支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComCompositeControl::CComCompositeControl](../Topic/CComCompositeControl::CComCompositeControl.md)|建構函式。|  
|[CComCompositeControl::~CComCompositeControl](../Topic/CComCompositeControl::~CComCompositeControl.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComCompositeControl::AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md)|呼叫這個方法通知或 unadvise 複合控制項裝載的控制項。|  
|[CComCompositeControl::CalcExtent](../Topic/CComCompositeControl::CalcExtent.md)|呼叫這個方法會計算中所用的對話方塊資源的 **HIMETRIC** 單位的大小來裝載複合控制項。|  
|[CComCompositeControl::Create](../Topic/CComCompositeControl::Create.md)|這個方法會呼叫以建立複合控制項之控制項的視窗。|  
|[CComCompositeControl::CreateControlWindow](../Topic/CComCompositeControl::CreateControlWindow.md)|呼叫這個方法會建立控制項的視窗和建議所有裝載的控制項。|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](../Topic/CComCompositeControl::SetBackgroundColorFromAmbient.md)|使用容器的背景色彩，呼叫這個方法會設定複合控制項的背景色彩。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComCompositeControl::m\_hbrBackground](../Topic/CComCompositeControl::m_hbrBackground.md)|背景筆刷。|  
|[CComCompositeControl::m\_hWndFocus](../Topic/CComCompositeControl::m_hWndFocus.md)|目前擁有焦點的視窗的控制代碼。|  
  
## 備註  
 從類別衍生的類別 `CComCompositeControl` ActiveX 繼承使用者控制項的功能。  從 `CComCompositeControl` 衍生的 ActiveX 控制項是標準的對話方塊中裝載。  控制項使用這些型別稱為"複合控制項，因為它們可以裝載其他控制項 \(原生 Windows 控制項和 ActiveX 控制項\)。  
  
 在建立`CComCompositeControl` 識別對話方塊資源使用複合控制項將會尋找子類別中的繫結值成員。  這項子類別的成員 IDD 設定為將做為控制項視窗對話方塊資源中的資源 ID。  下列是來自 `CComCompositeControl` 衍生自類別的類別必須包含可識別控制項視窗會使用的對話方塊資源資料成員的範例:  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/CPP/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  複合控制項永遠是視窗型控制項，不過，它們可以包含無視窗 \(Windowless\) 控制項。  
  
 `CComCompositeControl`實作的控制項都有預設的定位停駐行為安裝的衍生類別。  當控制項傳遞所選接收焦點為包含的應用程式，只要按下 TAB 鍵會使焦點通過所有複合控制項中所包含之控制項的循環，然後從複合控制項和到下一個項目定位順序容器的順序。  對話方塊資源取決於裝載控制項的定位順序並判斷選取中出現的順序。  
  
> [!NOTE]
>  若要快速鍵可以適當地使用 `CComCompositeControl`時，載入快速鍵對應表，因為控制項建立必要，可以快速鍵的控制代碼和數目回 [IOleControlImpl::GetControlInfo](../Topic/IOleControlImpl::GetControlInfo.md)終結和最後一個資料表，而放開控制項。  
  
## 範例  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/CPP/ccomcompositecontrol-class_2.h)]  
  
## 繼承階層架構  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)   
 [Class Overview](../../atl/atl-class-overview.md)