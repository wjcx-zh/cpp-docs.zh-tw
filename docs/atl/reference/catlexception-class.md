---
title: "CAtlException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs:
- C++
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
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
ms.openlocfilehash: 30c9235f16581c86ab5612522909dc366b1ce17e
ms.lasthandoff: 02/24/2017

---
# <a name="catlexception-class"></a>CAtlException 類別
這個類別會定義 ATL 例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlException
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlException::CAtlException](#catlexception)|建構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](#operator_hresult)|將轉換的 HRESULT 值的目前物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|HRESULT 物件所建立，用來儲存錯誤狀況的類型的變數。|  
  
## <a name="remarks"></a>備註  
 A`CAtlException`物件代表與 ATL 作業相關的例外狀況。 `CAtlException`類別包含儲存表示，轉換運算子，可讓您將處理例外狀況，就好像 HRESULT 的例外狀況原因的狀態碼的公用資料成員。  
  
 一般情況下，您會呼叫`AtlThrow`而不是建立`CAtlException`直接物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlexcept.h  
  
##  <a name="catlexception"></a>CAtlException::CAtlException  
 建構函式。  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>參數  
 `hr`  
 `HRESULT`錯誤碼。  
  
##  <a name="operator_hresult"></a>CAtlException::operator HRESULT 
 將轉換的 HRESULT 值的目前物件。  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>CAtlException::m_hr  
 `HRESULT`資料成員。  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>備註  
 將錯誤狀況的資料成員。 HRESULT 值由建構函式，設定[CAtlException::CAtlException](#catlexception)。  
  
## <a name="see-also"></a>另請參閱  
 [AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7)   
 [類別概觀](../../atl/atl-class-overview.md)

