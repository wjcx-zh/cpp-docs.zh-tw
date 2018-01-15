---
title: "CComObjectGlobal 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs: C++
helpviewer_keywords: CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d5264a2ab8e1bbc4c3f4eac4d83d096d91e8846
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 類別
這個類別會管理上包含的模組的參考計數程式`Base`物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class Base>
class CComObjectGlobal : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面呼叫也一樣。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|建構函式。|  
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectGlobal::AddRef](#addref)|實作全域`AddRef`。|  
|[CComObjectGlobal::QueryInterface](#queryinterface)|實作全域`QueryInterface`。|  
|[CComObjectGlobal::Release](#release)|實作全域**發行**。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|包含**HRESULT**在建構期間傳回`CComObjectGlobal`物件。|  
  
## <a name="remarks"></a>備註  
 `CComObjectGlobal`管理上包含的模組的參考計數程式`Base`物件。 `CComObjectGlobal`可確保只要模組並不會釋放，不會刪除您的物件。 整個模組上的參考計數歸零時，就只會移除您的物件。  
  
 例如，使用`CComObjectGlobal`，class factory 可以保存通用的全域物件共用的所有用戶端。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObjectGlobal`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="addref"></a>CComObjectGlobal::AddRef  
 物件的參考計數遞增 1。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷和測試。  
  
### <a name="remarks"></a>備註  
 根據預設，`AddRef`呼叫**_Module::Lock**，其中**_Module**的全域執行個體[CComModule](../../atl/reference/ccommodule-class.md)或從其衍生的類別。  
  
##  <a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal  
 建構函式。 呼叫`FinalConstruct`，然後設定[m_hResFinalConstruct](#m_hresfinalconstruct)至`HRESULT`傳回`FinalConstruct`。  
  
```
CComObjectGlobal(void* = NULL));
```  
  
### <a name="remarks"></a>備註  
 如果您有不衍生基底類別從[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，您必須提供自己`FinalConstruct`方法。 此解構函式會呼叫 `FinalRelease`。  
  
##  <a name="dtor"></a>CComObjectGlobal:: ~ CComObjectGlobal  
 解構函式。  
  
```
CComObjectGlobal();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct  
 包含`HRESULT`呼叫`FinalConstruct`在建構期間`CComObjectGlobal`物件。  
  
```
HRESULT m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectGlobal::QueryInterface  
 擷取要求的介面指標的指標。  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]所要求介面的 GUID。  
  
 `ppvObject`  
 [out]Iid，所識別的介面指標的指標或**NULL**如果找不到介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 `QueryInterface` 只處理 COM 對應表格中的介面。  
  
##  <a name="release"></a>CComObjectGlobal::Release  
 遞減參考計數物件的以 1。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 在偵錯組建**發行**傳回值，這個值可用於診斷和測試。 在非偵錯組建**發行**一律傳回 0。  
  
### <a name="remarks"></a>備註  
 根據預設，**發行**呼叫**_Module::Unlock**，其中**_Module**的全域執行個體[CComModule](../../atl/reference/ccommodule-class.md)或從其衍生的類別。  
  
## <a name="see-also"></a>請參閱  
 [CComObjectStack 類別](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [Ccomobject< 類別](../../atl/reference/ccomobject-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
