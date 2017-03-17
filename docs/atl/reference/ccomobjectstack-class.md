---
title: "CComObjectStack 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 0738eae13fdca5906596194016ce22812fbfcd36
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectstack-class"></a>CComObjectStack 類別
這個類別會建立暫存的 COM 物件，並提供它的架構實作**IUnknown**。  
  
## <a name="syntax"></a>語法  
  
```
template <class  Base>  
class CComObjectStack
 : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，如您想要在物件上支援從任何其他介面。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|建構函式。|  
|[CComObjectStack:: ~ CComObjectStack](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComObjectStack::AddRef](#addref)|傳回零。 在偵錯模式中，會呼叫`_ASSERTE`。|  
|[CComObjectStack::QueryInterface](#queryinterface)|傳回**E_NOINTERFACE**。 在偵錯模式中，會呼叫`_ASSERTE`。|  
|[CComObjectStack::Release](#release)|傳回零。 在偵錯模式中，會呼叫`_ASSERTE`。 ~|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|包含**HRESULT**在建構期間傳回`CComObjectStack`物件。|  
  
## <a name="remarks"></a>備註  
 `CComObjectStack`用來建立暫存的 COM 物件，並提供物件的架構實作**IUnknown**。 一般來說，物件作為一個函式 （也就，推入堆疊） 內的區域變數。 因為函數完成時，會終結物件，參考計數不會執行提高效率。  
  
 下列範例示範如何建立用於函式內的 COM 物件︰  
  
 [!code-cpp[NVC_ATL_COM&#42;](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]  
  
 暫存物件`Tempobj`推送至堆疊和函式完成時，會自動消失。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComObjectStack`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="addref"></a>CComObjectStack::AddRef  
 傳回零。  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>傳回值  
 傳回零。  
  
### <a name="remarks"></a>備註  
 在偵錯模式中，會呼叫`_ASSERTE`。  
  
##  <a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack  
 建構函式。  
  
```
CComObjectStack(void* = NULL);
```  
  
### <a name="remarks"></a>備註  
 呼叫`FinalConstruct`，然後設定[m_hResFinalConstruct](#m_hresfinalconstruct)至`HRESULT`傳回`FinalConstruct`。 如果您不具有衍生的基底類別從[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，您必須提供自己`FinalConstruct`方法。 此解構函式會呼叫 `FinalRelease`。  
  
##  <a name="dtor"></a>CComObjectStack:: ~ CComObjectStack  
 解構函式。  
  
```
CComObjectStack();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。  
  
##  <a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct  
 包含`HRESULT`從呼叫傳回`FinalConstruct`在建構期間`CComObjectStack`物件。  
  
```
HRESULT    m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>CComObjectStack::QueryInterface  
 傳回**E_NOINTERFACE**。  
  
```
HRESULT    QueryInterface(REFIID, void**)
 ;
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOINTERFACE**。  
  
### <a name="remarks"></a>備註  
 在偵錯模式中，會呼叫`_ASSERTE`。  
  
##  <a name="release"></a>CComObjectStack::Release  
 傳回零。  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>傳回值  
 傳回零。  
  
### <a name="remarks"></a>備註  
 在偵錯模式中，會呼叫`_ASSERTE`。  
  
## <a name="see-also"></a>另請參閱  
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 類別](../../atl/reference/ccomobject-class.md)   
 [CComObjectGlobal 類別](../../atl/reference/ccomobjectglobal-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

