---
title: "CComSafeDeleteCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs:
- C++
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df86d5219940ffc1dd3c34f47920675014eefd13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 類別
這個類別會提供方法來取得及釋放重要區段物件的擁有權。  
  
## <a name="syntax"></a>語法  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|建構函式。|  
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|建立並初始化的關鍵區段物件。|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|取得重要區段物件的擁有權。|  
|[CComSafeDeleteCriticalSection::Term](#term)|釋放重要區段物件所使用的系統資源。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|旗標是否內部**CRITICAL_SECTION**物件已初始化。|  
  
## <a name="remarks"></a>備註  
 `CComSafeDeleteCriticalSection`衍生自類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 不過，`CComSafeDeleteCriticalSection`提供額外的安全機制，透過[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。  
  
 執行個體時`CComSafeDeleteCriticalSection`超出範圍或明確從記憶體中刪除，基礎關鍵區段物件將會自動清除是否仍然有效。 此外， [CComSafeDeleteCriticalSection::Term](#term)方法將會依正常程序結束，如果基礎關鍵區段物件尚未配置或已從記憶體釋放。  
  
 請參閱[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)如需有關關鍵區段的 helper 類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 建構函式。  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>備註  
 設定[m_bInitialized](#m_binitialized)資料成員，才能**false**。  
  
##  <a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection  
 解構函式。  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>備註  
 釋出內部**CRITICAL_SECTION**物件從記憶體中，如果[m_bInitialized](#m_binitialized)資料成員設定為**true**。  
  
##  <a name="init"></a>CComSafeDeleteCriticalSection::Init  
 呼叫的基底類別實作[Init](/visualstudio/debugger/init)並設定[m_bInitialized](#m_binitialized)至**true**如果成功的話。  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的結果[CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init)。  
  
##  <a name="lock"></a>CComSafeDeleteCriticalSection::Lock  
呼叫的基底類別實作[鎖定](ccomcriticalsection-class.md#lock)。  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的結果[CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。  
  
### <a name="remarks"></a>備註  
 這個方法會假設[m_bInitialized](#m_binitialized)資料成員設定為**true**進入時。 如果不符合此 condidtion 偵錯組建中產生判斷提示。  
  
 如需行為的函式的詳細資訊，請參閱[CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。  
  
##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized  
 旗標是否內部**CRITICAL_SECTION**物件已初始化。  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>備註  
 **M_bInitialized**資料成員用來追蹤的基礎有效性**CRITICAL_SECTION**物件相關聯[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)類別。 基礎**CRITICAL_SECTION**物件不會嘗試釋放記憶體，如果這個旗標未設為**true**。  
  
##  <a name="term"></a>CComSafeDeleteCriticalSection::Term  
 呼叫的基底類別實作[CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)如果內部**CRITICAL_SECTION**物件是否有效。  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的結果[CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term)，或**S_OK**如果[m_bInitialized](#m_binitialized)設**false**進入時。  
  
### <a name="remarks"></a>備註  
 您可以放心呼叫此方法，即使內部**CRITICAL_SECTION**物件無效。 這個類別的解構函式會呼叫這個方法，如果[m_bInitialized](#m_binitialized)資料成員設定為**true**。  
  
## <a name="see-also"></a>請參閱  
 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
