---
title: "CComGITPtr Class | Microsoft Docs"
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
  - "ATL::CComGITPtr<T>"
  - "CComGITPtr"
  - "ATL.CComGITPtr"
  - "ATL.CComGITPtr<T>"
  - "ATL::CComGITPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComGITPtr class"
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComGITPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會處理方法提供介面指標和全域介面表 \(GIT\)。  
  
## 語法  
  
```  
  
      template <  
   class T   
>  
class CComGITPtr  
```  
  
#### 參數  
 `T`  
 在 GIT 要儲存之介面指標的型別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComGITPtr::CComGITPtr](../Topic/CComGITPtr::CComGITPtr.md)|建構函式。|  
|[CComGITPtr::~CComGITPtr](../Topic/CComGITPtr::~CComGITPtr.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComGITPtr::Attach](../Topic/CComGITPtr::Attach.md)|呼叫這個方法會註冊介面指標在全域介面表 \(GIT\) 中。|  
|[CComGITPtr::CopyTo](../Topic/CComGITPtr::CopyTo.md)|呼叫這個方法會從介面全域資料表 \(GIT\) 的介面加入至傳入至的指標。|  
|[CComGITPtr::Detach](../Topic/CComGITPtr::Detach.md)|呼叫這個方法分開 `CComGITPtr` 物件的介面。|  
|[CComGITPtr::GetCookie](../Topic/CComGITPtr::GetCookie.md)|呼叫這個方法會從 `CComGITPtr` 物件的 Cookie。|  
|[CComGITPtr::Revoke](../Topic/CComGITPtr::Revoke.md)|呼叫這個方法會從介面全域資料表 \(GIT\) 移除介面。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComGITPtr::operator DWORD](../Topic/CComGITPtr::operator%20DWORD.md)|傳回從 `CComGITPtr` 物件的 Cookie。|  
|[CComGITPtr::operator \=](../Topic/CComGITPtr::operator%20=.md)|指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComGITPtr::m\_dwCookie](../Topic/CComGITPtr::m_dwCookie.md)|Cookie。|  
  
## 備註  
 彙總 \(Aggregate\) 無限制執行緒封送處理器和需要使用衍生自其他物件的介面指標的物件必須採取其他步驟以確保介面正確封送處理。  通常，每次使用，這需要儲存介面指標在 GIT 和取得指標從 GIT 它。  提供類別 `CComGITPtr` 可協助您在 GIT 儲存的介面指標。  
  
> [!NOTE]
>  全域介面表安裝只適用於 Windows 95 和 DCOM 1.1 版 \(含\) 以後版本中， Windows 98、Windows NT 4.0 Service Pack 3 \(含\) 以後版本和 Windows 2000。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [無限制執行緒封送處理器](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Accessing Interfaces Across Apartments](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [When to Use the Global Interface Table](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Class Overview](../../atl/atl-class-overview.md)