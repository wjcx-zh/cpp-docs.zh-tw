---
title: "CSnapInItemImpl Class | Microsoft Docs"
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
  - "CSnapInItemImpl"
  - "ATL.CSnapInItemImpl"
  - "ATL::CSnapInItemImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSnapInItemImpl class"
  - "snap-ins"
  - "snap-ins, ATL support for"
  - "snap-ins, data items"
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSnapInItemImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作嵌入式管理單元的節點物件的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
BOOL bIsExtension= FALSE  
>  
class ATL_NO_VTABLE CSnapInItemImpl :  
public CSnapInItem  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `CSnapInItemImpl`。  
  
 *bIsExtension*  
 **是** ，如果物件是的嵌入式管理單元的副檔名，否則 **否**。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSnapInItemImpl::CSnapInItemImpl](../Topic/CSnapInItemImpl::CSnapInItemImpl.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSnapInItemImpl::AddMenuItems](../Topic/CSnapInItemImpl::AddMenuItems.md)|將功能表項目加入至內容功能表。|  
|[CSnapInItemImpl::Command](../Topic/CSnapInItemImpl::Command.md)|呼叫主控台，當自訂功能表項目已選取。|  
|[CSnapInItemImpl::CreatePropertyPages](../Topic/CSnapInItemImpl::CreatePropertyPages.md)|將頁面加入至嵌入式管理單元的屬性工作表。|  
|[CSnapInItemImpl::FillData](../Topic/CSnapInItemImpl::FillData.md)|如需嵌入式管理單元的物件複本資訊加入至指定的資料流中。|  
|[CSnapInItemImpl::GetResultPaneInfo](../Topic/CSnapInItemImpl::GetResultPaneInfo.md)|擷取嵌入式管理單元的 **RESULTDATAITEM** 結構。|  
|[CSnapInItemImpl::GetResultViewType](../Topic/CSnapInItemImpl::GetResultViewType.md)|判斷 \[結果\] 窗格所使用的檢視類型。|  
|[CSnapInItemImpl::GetScopePaneInfo](../Topic/CSnapInItemImpl::GetScopePaneInfo.md)|擷取嵌入式管理單元的 **SCOPEDATAITEM** 結構。|  
|[CSnapInItemImpl::Notify](../Topic/CSnapInItemImpl::Notify.md)|呼叫主控台告知使用者採取的動作嵌入式管理單元。|  
|[CSnapInItemImpl::QueryPagesFor](../Topic/CSnapInItemImpl::QueryPagesFor.md)|請呼叫這個嵌入式管理單元的節點是否支援屬性頁。|  
|[CSnapInItemImpl::SetMenuInsertionFlags](../Topic/CSnapInItemImpl::SetMenuInsertionFlags.md)|修改嵌入式管理單元物件功能表來將旗標。|  
|[CSnapInItemImpl::SetToolbarButtonInfo](../Topic/CSnapInItemImpl::SetToolbarButtonInfo.md)|設定指定的工具列按鈕的資訊。|  
|[CSnapInItemImpl::UpdateMenuState](../Topic/CSnapInItemImpl::UpdateMenuState.md)|更新內容功能表項目的狀態。|  
|[CSnapInItemImpl::UpdateToolbarButton](../Topic/CSnapInItemImpl::UpdateToolbarButton.md)|更新指定的工具列按鈕的狀態。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CSnapInItemImpl::m\_bstrDisplayName](../Topic/CSnapInItemImpl::m_bstrDisplayName.md)|嵌入式管理單元的物件名稱。|  
|[CSnapInItemImpl::m\_resultDataItem](../Topic/CSnapInItemImpl::m_resultDataItem.md)|`CSnapInItemImpl` 物件使用的視窗 **RESULTDATAITEM** 結構。|  
|[CSnapInItemImpl::m\_scopeDataItem](../Topic/CSnapInItemImpl::m_scopeDataItem.md)|`CSnapInItemImpl` 物件使用的視窗 **SCOPEDATAITEM** 結構。|  
  
## 備註  
 `CSnapInItemImpl` 為嵌入式管理單元會提供物件的基底實作，例如將功能表項目和工具列，，和向前這個嵌入式管理單元的節點順序為適當的處理常式中運作。  這些實作功能時使用的數個不同介面並對應型別。  預設實作會處理告知傳送至節點可以判斷所衍生類別的正確執行個體會轉送訊息回應至正確的執行個體。  
  
## 繼承階層架構  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## 需求  
 **Header:** atlsnap.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)