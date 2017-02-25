---
title: "IProvideClassInfo2Impl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IProvideClassInfo2"
  - "ATL.IProvideClassInfo2Impl"
  - "IProvideClassInfo2Impl"
  - "ATL::IProvideClassInfo2Impl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class information, ATL"
  - "IProvideClassInfo2 ATL implementation"
  - "IProvideClassInfo2Impl class"
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IProvideClassInfo2Impl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) 和 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) 方法的預設實作。  
  
## 語法  
  
```  
  
      template <  
   const CLSID* pcoclsid,  
   const IID* psrcid,  
   const GUID* plibid = &CAtlModule::m_libid,  
   WORD wMajor = 1,  
   WORD wMinor = 0,  
   class tihclass = CComTypeInfoHolder   
>  
class ATL_NO_VTABLE IProvideClassInfo2Impl :  
   public IProvideClassInfo2  
```  
  
#### 參數  
 *pcoclsid*  
 至 Coclass 的類別識別項的指標。  
  
 *psrcid*  
 的識別項的指標 Coclass 的預設輸出的分配介面 \(Dispinterface\) 的。  
  
 `plibid`  
 其包含有關此介面的資訊型別程式庫的 GUID 的指標。  根據預設，這個伺服器層級的型別程式庫中傳遞。  
  
 `wMajor`  
 型別程式庫的主要版本。  預設值為 1。  
  
 `wMinor`  
 型別程式庫的次要版本。  預設值為 0。  
  
 `tihclass`  
 用於類別處理 Coclass 的型別資訊。  預設值是 `CComTypeInfoHolder`。  
  
## Members  
  
### 建構函式  
  
|名稱|描述|  
|--------|--------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](../Topic/IProvideClassInfo2Impl::IProvideClassInfo2Impl.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IProvideClassInfo2Impl::GetClassInfo](../Topic/IProvideClassInfo2Impl::GetClassInfo.md)|擷取 **ITypeInfo** 指標 Coclass 的型別資訊。|  
|[IProvideClassInfo2Impl::GetGUID](../Topic/IProvideClassInfo2Impl::GetGUID.md)|擷取物件的外送分配介面的 GUID。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[IProvideClassInfo2Impl::\_tih](../Topic/IProvideClassInfo2Impl::_tih.md)|處理 Coclass 的型別資訊。|  
  
## 備註  
 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) 介面會加入 `GetGUID` 方法擴充 [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) 。  這個方法允許用戶端擷取其預設事件集合的物件之輸出介面的 IID。  類別提供 `IProvideClassInfo2Impl`**IProvideClassInfo** 和 `IProvideClassInfo2` 方法的預設實作。  
  
 `IProvideClassInfo2Impl` 包含處理 Coclass 的型別資訊的型別 `CComTypeInfoHolder` 的靜態成員。  
  
## 繼承階層架構  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)