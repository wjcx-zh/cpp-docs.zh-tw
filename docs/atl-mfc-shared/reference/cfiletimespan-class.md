---
title: "CFileTimeSpan 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da47f0113ec2e36f6df4afa32f6aff84d5ee6dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 類別
這個類別會提供管理相對日期和時間值與檔案相關聯的方法。  
  
## <a name="syntax"></a>語法  
  
```
class CFileTimeSpan
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|呼叫此方法以擷取的時間範圍，從`CFileTimeSpan`物件。|  
|[CFileTimeSpan::SetTimeSpan](#settimespan)|呼叫此方法以設定的時間範圍內`CFileTimeSpan`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileTimeSpan::operator-](#operator_-)|在上執行減法`CFileTimeSpan`物件。|  
|[CFileTimeSpan::operator ！ =](#operator_neq)|比較兩個 `CFileTimeSpan` 物件是否不相等。|  
|[CFileTimeSpan::operator +](#operator_add)|在上執行加法`CFileTimeSpan`物件。|  
|[CFileTimeSpan::operator + =](#operator_add_eq)|在上執行加法`CFileTimeSpan`物件，並將結果指派給目前的物件。|  
|[CFileTimeSpan::operator&lt;](#operator_lt)|比較兩個`CFileTimeSpan`物件來判斷兩者較小者。|  
|[CFileTimeSpan::operator&lt;=](#operator_lt_eq)|比較兩個`CFileTimeSpan`物件來判斷是否相等或較小者。|  
|[CFileTimeSpan::operator =](#operator_eq)|指派運算子。|  
|[CFileTimeSpan::operator =](#operator_-_eq)|在上執行減法`CFileTimeSpan`物件，並將結果指派給目前的物件。|  
|[CFileTimeSpan::operator = =](#operator_eq_eq)|比較兩個 `CFileTimeSpan` 物件是否相等。|  
|[CFileTimeSpan::operator&gt;](#operator_gt)|比較兩個`CFileTimeSpan`物件來判斷較大。|  
|[CFileTimeSpan::operator&gt;=](#operator_gt_eq)|比較兩個`CFileTimeSpan`物件來判斷是否相等或較大。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供用來管理相對期間方法的時間經常遇到執行時有關的作業時建立、 最後一次存取或上次修改檔案。 這個類別的方法通常用於搭配[CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)物件。  
  
## <a name="example"></a>範例  
 請參閱範例的[CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atltime.h  
  
##  <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan  
 建構函式。  
  
```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 現有的 `CFileTimeSpan` 物件。  
  
 `nSpan`  
 一段時間 （毫秒）。  
  
### <a name="remarks"></a>備註  
 `CFileTimeSpan`物件可由使用現有`CFileTimeSpan`物件，或以 64 位元值。 預設建構函式設定的時間範圍為 0。  
  
##  <a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan  
 呼叫此方法以擷取的時間範圍，從`CFileTimeSpan`物件。  
  
```
LONGLONG GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的時間範圍，以毫秒為單位。  
  
##  <a name="operator_-"></a>CFileTimeSpan::operator-  
 在上執行減法**CFileTimeSpan**物件。  
  
```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CFileTimeSpan`物件，表示兩個時間範圍之間的差異的結果。  
  
##  <a name="operator_neq"></a>CFileTimeSpan::operator ！ =  
 比較兩個 `CFileTimeSpan` 物件是否不相等。  
  
```
bool operator!=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要比較的 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**所比較的項目是否不等於`CFileTimeSpan`物件; 否則**false**。  
  
##  <a name="operator_add"></a>CFileTimeSpan::operator +  
 在上執行加法`CFileTimeSpan`物件。  
  
```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CFileTimeSpan`包含總和的兩個時間跨越的物件。  
  
##  <a name="operator_add_eq"></a>CFileTimeSpan::operator + =  
 在上執行加法`CFileTimeSpan`物件，並將結果指派給目前的物件。  
  
```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CFileTimeSpan`包含總和的兩個時間跨越的物件。  
  
##  <a name="operator_lt"></a>CFileTimeSpan::operator&lt;  
 比較兩個`CFileTimeSpan`物件來判斷兩者較小者。  
  
```
bool operator<(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要比較的 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**的第一個物件是否小於 （也就是代表較短的時間） 第二個，否則**false**。  
  
##  <a name="operator_lt_eq"></a>CFileTimeSpan::operator&lt;=  
 比較兩個`CFileTimeSpan`物件來判斷是否相等或較小者。  
  
```
bool operator<=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要比較的 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果第一個物件小於 （也就是代表較短的時間期間） 或等於第二個，否則**false**。  
  
##  <a name="operator_eq"></a>CFileTimeSpan::operator =  
 指派運算子。  
  
```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CFileTimeSpan`物件。  
  
##  <a name="operator_-_eq"></a>CFileTimeSpan::operator =  
 在上執行減法`CFileTimeSpan`物件，並將結果指派給目前的物件。  
  
```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CFileTimeSpan`物件。  
  
##  <a name="operator_eq_eq"></a>CFileTimeSpan::operator = =  
 比較兩個 `CFileTimeSpan` 物件是否相等。  
  
```
bool operator==(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要比較的 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果物件相等，否則為**false**。  
  
##  <a name="operator_gt"></a>CFileTimeSpan::operator&gt;  
 比較兩個`CFileTimeSpan`物件來判斷較大。  
  
```
bool operator>(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要比較的 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**是否大於第一個物件 （也就是代表較長的時間期間） 第二個，否則**false**。  
  
##  <a name="operator_gt_eq"></a>CFileTimeSpan::operator&gt;=  
 比較兩個`CFileTimeSpan`物件來判斷是否相等或較大。  
  
```
bool operator>=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>參數  
 `span`  
 要比較的 `CFileTimeSpan` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**是否大於第一個物件 （也就是代表較長的時間期間） 或等於第二個，否則**false**。  
  
##  <a name="settimespan"></a>CFileTimeSpan::SetTimeSpan  
 呼叫此方法以設定的時間範圍內`CFileTimeSpan`物件。  
  
```
void SetTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>參數  
 `nSpan`  
 以毫秒為單位的時間範圍的新值。  
  
## <a name="see-also"></a>請參閱  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)


