---
title: "COleDispatchDriver Class | Microsoft Docs"
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
  - "COleDispatchDriver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation clients, implementing Automation"
  - "COleDispatchDriver class"
  - "OLE dispatch interface"
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDispatchDriver Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 OLE Automation 的用戶端。  
  
## 語法  
  
```  
class COleDispatchDriver  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDispatchDriver::COleDispatchDriver](../Topic/COleDispatchDriver::COleDispatchDriver.md)|建構 `COleDispatchDriver` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDispatchDriver::AttachDispatch](../Topic/COleDispatchDriver::AttachDispatch.md)|附加 `COleDispatchDriver` 物件的 `IDispatch` 連接。|  
|[COleDispatchDriver::CreateDispatch](../Topic/COleDispatchDriver::CreateDispatch.md)|建立 `IDispatch` 連接並將其附加至 `COleDispatchDriver` 物件。|  
|[COleDispatchDriver::DetachDispatch](../Topic/COleDispatchDriver::DetachDispatch.md)|中斷連接， `IDispatch` ，而不需釋放它。|  
|[COleDispatchDriver::GetProperty](../Topic/COleDispatchDriver::GetProperty.md)|取得自動屬性。|  
|[COleDispatchDriver::InvokeHelper](../Topic/COleDispatchDriver::InvokeHelper.md)|呼叫的 Automation Helper 方法。|  
|[COleDispatchDriver::ReleaseDispatch](../Topic/COleDispatchDriver::ReleaseDispatch.md)|釋放 `IDispatch` 連接。|  
|[COleDispatchDriver::SetProperty](../Topic/COleDispatchDriver::SetProperty.md)|設定自動屬性。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[COleDispatchDriver::operator \=](../Topic/COleDispatchDriver::operator%20=.md)|複製來源值。 `COleDispatchDriver` 物件。|  
|[COleDispatchDriver::operator LPDISPATCH](../Topic/COleDispatchDriver::operator%20LPDISPATCH.md)|存取基礎 `IDispatch` 指標。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleDispatchDriver::m\_bAutoRelease](../Topic/COleDispatchDriver::m_bAutoRelease.md)|指定是否要釋放 `IDispatch` 在 `ReleaseDispatch` 或物件解構。|  
|[COleDispatchDriver::m\_lpDispatch](../Topic/COleDispatchDriver::m_lpDispatch.md)|指示指標 `IDispatch` 介面附加至這個 `COleDispatchDriver`。|  
  
## 備註  
 `COleDispatchDriver` 不具有基底類別。  
  
 OLE 分派介面提供對物件的方法和屬性。  `COleDispatchDriver` 附加成員函式，中斷連接，建立，然後釋放型別 `IDispatch`的分派介面。  其他成員函式使用變數引數清單簡化呼叫 **IDispatch::Invoke**。  
  
 您可以直接使用此類別，但是，加入類別精靈所建立的類別通常是用它。  當您建立新的 C\+\+ 藉由匯入型別程式庫時，新的類別 `COleDispatchDriver`從衍生。  
  
 如需使用 `COleDispatchDriver`的資訊，請參閱下列文件:  
  
-   [Automation 用戶端](../../mfc/automation-clients.md)  
  
-   [Automation 伺服程式](../../mfc/automation-servers.md)  
  
## 繼承階層架構  
 `COleDispatchDriver`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [MFC 範例 CALCDRIV](../../top/visual-cpp-samples.md)   
 [MFC ACDUAL 範例](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)