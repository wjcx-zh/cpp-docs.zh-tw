---
title: "IOleObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IOleObjectImpl"
  - "ATL.IOleObjectImpl<T>"
  - "ATL::IOleObjectImpl"
  - "ATL::IOleObjectImpl<T>"
  - "IOleObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], communication between container and control"
  - "IOleObject, ATL 實作"
  - "IOleObjectImpl class"
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 **IUnknown** 和容器是與控制項溝通的主要介面。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IOleObjectImpl :  
public IOleObject  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IOleObjectImpl`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IOleObjectImpl::Advise](../Topic/IOleObjectImpl::Advise.md)|建立具有控制諮詢連接。|  
|[IOleObjectImpl::Close](../Topic/IOleObjectImpl::Close.md)|從執行變更控制項狀態載入至。|  
|[IOleObjectImpl::DoVerb](../Topic/IOleObjectImpl::DoVerb.md)|告知控制項執行其所列舉的其中一個動作。|  
|[IOleObjectImpl::DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md)|指示控制項捨棄維護所有復原狀態。|  
|[IOleObjectImpl::DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md)|指示控制項從檢視中移除它的使用者介面。|  
|[IOleObjectImpl::DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md)|執行控制項以及安裝視窗，但是，安裝控制項之使用者介面。|  
|[IOleObjectImpl::DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md)|在另一個視窗讓控制項開啟進行編輯。|  
|[IOleObjectImpl::DoVerbPrimary](../Topic/IOleObjectImpl::DoVerbPrimary.md)|當使用者按兩下控制項時，執行指定的動作。  控制項會定義動作，通常是就地啟動的控制項。|  
|[IOleObjectImpl::DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md)|顯示新插入的控制項給使用者。|  
|[IOleObjectImpl::DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md)|啟動就地的控制項並顯示控制項的使用者介面 \(UI\)，例如功能表和工具列。|  
|[IOleObjectImpl::EnumAdvise](../Topic/IOleObjectImpl::EnumAdvise.md)|列舉型別 \(Enumeration\) 控制諮詢連接。|  
|[IOleObjectImpl::EnumVerbs](../Topic/IOleObjectImpl::EnumVerbs.md)|列舉型別是由控制項的動作。|  
|[IOleObjectImpl::GetClientSite](../Topic/IOleObjectImpl::GetClientSite.md)|擷取控制項的用戶端站台上。|  
|[IOleObjectImpl::GetClipboardData](../Topic/IOleObjectImpl::GetClipboardData.md)|從剪貼簿擷取資料。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::GetExtent](../Topic/IOleObjectImpl::GetExtent.md)|擷取控制項的顯示區域的程度。|  
|[IOleObjectImpl::GetMiscStatus](../Topic/IOleObjectImpl::GetMiscStatus.md)|擷取控制項的狀態。|  
|[IOleObjectImpl::GetMoniker](../Topic/IOleObjectImpl::GetMoniker.md)|擷取控制項的 Moniker。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::GetUserClassID](../Topic/IOleObjectImpl::GetUserClassID.md)|擷取控制項的類別識別項。|  
|[IOleObjectImpl::GetUserType](../Topic/IOleObjectImpl::GetUserType.md)|擷取控制項的使用者型別名稱。|  
|[IOleObjectImpl::InitFromData](../Topic/IOleObjectImpl::InitFromData.md)|初始化一個從選取之資料的控制項。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::IsUpToDate](../Topic/IOleObjectImpl::IsUpToDate.md)|檢查控制項是否為最新的。  ATL 實作會傳回 `S_OK`。|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](../Topic/IOleObjectImpl::OnPostVerbDiscardUndo.md)|呼叫 [DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md) 在復原狀態後捨棄。|  
|[IOleObjectImpl::OnPostVerbHide](../Topic/IOleObjectImpl::OnPostVerbHide.md)|呼叫 [DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md) 在控制項之後隱藏。|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](../Topic/IOleObjectImpl::OnPostVerbInPlaceActivate.md)|呼叫 [DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md) 在控制項之後就地啟動。|  
|[IOleObjectImpl::OnPostVerbOpen](../Topic/IOleObjectImpl::OnPostVerbOpen.md)|呼叫 [DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md) ，在控制項中進行編輯時開啟在另一個視窗之後。|  
|[IOleObjectImpl::OnPostVerbShow](../Topic/IOleObjectImpl::OnPostVerbShow.md)|呼叫 [DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md) ，在控制項可見之後。|  
|[IOleObjectImpl::OnPostVerbUIActivate](../Topic/IOleObjectImpl::OnPostVerbUIActivate.md)|呼叫 [DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md) ，在控制項之使用者介面 \(UI\) 啟動之後。|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](../Topic/IOleObjectImpl::OnPreVerbDiscardUndo.md)|呼叫 [DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md) 在復原狀態之前遭到捨棄。|  
|[IOleObjectImpl::OnPreVerbHide](../Topic/IOleObjectImpl::OnPreVerbHide.md)|呼叫 [DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md) 於控制項中隱藏。|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](../Topic/IOleObjectImpl::OnPreVerbInPlaceActivate.md)|呼叫 [DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md) 於控制項就地啟動。|  
|[IOleObjectImpl::OnPreVerbOpen](../Topic/IOleObjectImpl::OnPreVerbOpen.md)|呼叫 [DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md) ，在控制項中進行編輯時開啟在另一個視窗之前。|  
|[IOleObjectImpl::OnPreVerbShow](../Topic/IOleObjectImpl::OnPreVerbShow.md)|呼叫 [DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md) ，在控制項成為可見的。|  
|[IOleObjectImpl::OnPreVerbUIActivate](../Topic/IOleObjectImpl::OnPreVerbUIActivate.md)|呼叫 [DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md) ，在控制項之使用者介面 \(UI\) 啟動之前。|  
|[IOleObjectImpl::SetClientSite](../Topic/IOleObjectImpl::SetClientSite.md)|告知其用戶端網站的控制項容器的。|  
|[IOleObjectImpl::SetColorScheme](../Topic/IOleObjectImpl::SetColorScheme.md)|建議色彩配置給控制項的應用程式，，如果有的話。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::SetExtent](../Topic/IOleObjectImpl::SetExtent.md)|設定控制項顯示區域的程度。|  
|[IOleObjectImpl::SetHostNames](../Topic/IOleObjectImpl::SetHostNames.md)|指示控制項容器應用程式和文件容器的名稱。|  
|[IOleObjectImpl::SetMoniker](../Topic/IOleObjectImpl::SetMoniker.md)|指示控制項所需的 Moniker 就是。  ATL 實作會傳回 **E\_NOTIMPL**。|  
|[IOleObjectImpl::Unadvise](../Topic/IOleObjectImpl::Unadvise.md)|使用控制項刪除諮詢連接。|  
|[IOleObjectImpl::Update](../Topic/IOleObjectImpl::Update.md)|更新控制項。  ATL 實作會傳回 `S_OK`。|  
  
## 備註  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) 介面是容器與控制項溝通的主要介面。  類別 `IOleObjectImpl` 提供這個介面的預設實作並透過傳送訊息至實作 **IUnknown** 傾印裝置偵錯組建。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)