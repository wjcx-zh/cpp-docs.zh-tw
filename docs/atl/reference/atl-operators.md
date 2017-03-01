---
title: "ATL 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: 16
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 87aadf7aacc31ded165a8e1380823cb20e614fb1
ms.lasthandoff: 02/24/2017

---
# <a name="atl-operators"></a>ATL 運算子
此章節包含 ATL 全域運算子參考主題。  
  
|運算子|說明|  
|--------------|-----------------|  
|[運算子 = =](#operator_eq_eq)|比較兩個`CSid`物件或`SID`結構是否相等。|  
|[運算子 ！ =](#operator_neq)|比較兩個`CSid`物件或`SID`結構是否不相等。|  
|[運算子](#operator_lt)|如果測試`CSid`物件或`SID`運算子左邊的結構是小於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
|[運算子 >](#operator_gt)|如果測試`CSid`物件或`SID`結構運算子的左側大於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
|[運算子<>](#operator_lt__eq)|如果測試`CSid`物件或`SID`結構運算子的左側小於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
|[運算子 > =](#operator_gt__eq)|如果測試`CSid`物件或`SID`運算子左邊的結構是大於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
  
 這些運算子會在檔案 atlsecurity.h 中定義。  
  
##  <a name="a-nameoperatoreqeqa--operator-"></a><a name="operator_eq_eq"></a>運算子 = =  
 比較`CSid`物件或`SID`（安全性識別碼） 結構是否相等。  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**物件是否相等，如果**false**是否不相等。  
  
##  <a name="a-nameoperatorneqa--operator-"></a><a name="operator_neq"></a>運算子 ！ =  
 比較`CSid`物件或`SID`（安全性識別碼） 結構是否不相等。  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**物件是否不相等，如果**false**是否相等。  
  
##  <a name="a-nameoperatorlta--operator-"></a><a name="operator_lt"></a>運算子  
 如果測試`CSid`物件或`SID`運算子左邊的結構是小於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果位址`lhs`物件是小於的位址`rhs`物件， **false**否則。  
  
### <a name="remarks"></a>備註  
 這個運算子處理程式碼的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。  
  
##  <a name="a-nameoperatorgta--operator-"></a><a name="operator_gt"></a>運算子 >  
 如果測試`CSid`物件或`SID`結構運算子的左側大於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果位址`lhs`大於位址`rhs`， **false**否則。  
  
### <a name="remarks"></a>備註  
 這個運算子處理程式碼的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。  
  
##  <a name="a-nameoperatorlteqa--operator-"></a><a name="operator_lt__eq"></a>運算子<=></=>  
 如果測試`CSid`物件或`SID`結構運算子的左側小於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果位址`lhs`小於或等於的位址`rhs`， **false**否則。  
  
### <a name="remarks"></a>備註  
 這個運算子處理程式碼的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。  
  
##  <a name="a-nameoperatorgteqa--operator-"></a><a name="operator_gt__eq"></a>運算子 > =  
 如果測試`CSid`物件或`SID`運算子左邊的結構是大於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果位址`lhs`大於或等於的位址`rhs`， **false**否則。  
  
### <a name="remarks"></a>備註  
 這個運算子處理程式碼的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。




