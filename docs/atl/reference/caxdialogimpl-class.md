---
title: "CAxDialogImpl Class | Microsoft Docs"
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
  - "ATL::CAxDialogImpl"
  - "ATL.CAxDialogImpl"
  - "CAxDialogImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 對話方塊"
  - "CAxDialogImpl class"
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAxDialogImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作對話方塊 \(強制回應或非強制回應\) 裝載 ActiveX 控制項。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class TBase= CWindow  
>  
class ATL_NO_VTABLE CAxDialogImpl :  
public CDialogImplBaseT< TBase>  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `CAxDialogImpl`。  
  
 *TBase*  
 **CDialogImplBaseT**基本的視窗類別。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAxDialogImpl::AdviseSinkMap](../Topic/CAxDialogImpl::AdviseSinkMap.md)|呼叫這個方法通知或 unadvise 物件中接收對應事件對應中的所有項目。|  
|[CAxDialogImpl::Create](../Topic/CAxDialogImpl::Create.md)|呼叫這個方法會建立非強制回應對話方塊。|  
|[CAxDialogImpl::DestroyWindow](../Topic/CAxDialogImpl::DestroyWindow.md)|呼叫這個方法會終結非強制回應對話方塊。|  
|[CAxDialogImpl::DoModal](../Topic/CAxDialogImpl::DoModal.md)|呼叫這個方法會建立強制回應對話方塊。|  
|[CAxDialogImpl::EndDialog](../Topic/CAxDialogImpl::EndDialog.md)|呼叫這個方法會終結強制回應對話方塊。|  
|[CAxDialogImpl::GetDialogProc](../Topic/CAxDialogImpl::GetDialogProc.md)|呼叫這個方法取得指標 `DialogProc` 回呼函式。|  
|[CAxDialogImpl::GetIDD](../Topic/CAxDialogImpl::GetIDD.md)|呼叫這個方法會取得對話方塊樣板資源 ID。|  
|[CAxDialogImpl::IsDialogMessage](../Topic/CAxDialogImpl::IsDialogMessage.md)|呼叫這個方法會決定訊息是否為這個對話方塊中使用，則為，如果它是，處理訊息。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAxDialogImpl::m\_bModal](../Topic/CAxDialogImpl::m_bModal.md)|只存在於的變數偵錯組建及設定為 true，則對話方塊會強制回應。|  
  
## 備註  
 `CAxDialogImpl` 允許您建立強制回應或非強制回應對話方塊。  `CAxDialogImpl` 提供對話方塊程序，使用預設的訊息對應會用來導向訊息給適當的處理常式。  
  
 `CAxDialogImpl` 從 `CDialogImplBaseT`衍生，從 *TBase* \(根據預設， `CWindow`\) 和 `CMessageMap`又衍生自。  
  
 您的類別必須定義指定對話方塊樣板資源 ID. 的 IDD 成員  例如，將使用 \[**加入類別**\] 對話方塊的 ATL 對話方塊物件會自動將下列行加入至類別:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/CPP/caxdialogimpl-class_1.h)]  
  
 其中 `MyDialog` 是 ATL 對話方塊精靈\] 中所輸入的 \[**簡短名稱**\] 。  
  
 請參閱 [實作對話方塊](../../atl/implementing-a-dialog-box.md) 以取得詳細資訊。  
  
 請注意在強制回應對話方塊的 ActiveX 控制項建立 `CAxDialogImpl` 不支援快速鍵。  使用自己的訊息迴圈，為了支援對話方塊的快速鍵建立 `CAxDialogImpl`，建立非強制回應對話方塊，然後，在這種情況下，接收訊息之後使用 [CAxDialogImpl::IsDialogMessage](../Topic/CAxDialogImpl::IsDialogMessage.md) 從佇列處理快速鍵。  
  
 如需 `CAxDialogImpl`的資訊，請參閱 [ATL 控制項內含項目 FAQ](../../atl/atl-control-containment-faq.md)。  
  
## 繼承階層架構  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [CDialogImpl Class](../../atl/reference/cdialogimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)