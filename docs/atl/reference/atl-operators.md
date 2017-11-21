---
title: "ATL 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords: operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46bc674a65e2ffc946a4806ce1440fec6e14c355
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="atl-operators"></a>ATL 運算子
此章節包含 ATL 全域運算子參考主題。  
  
|運算子|說明|  
|--------------|-----------------|  
|[運算子 = =](#operator_eq_eq)|比較兩個`CSid`物件或`SID`結構是否相等。|  
|[運算子 ！ =](#operator_neq)|比較兩個`CSid`物件或`SID`結構是否不相等。|  
|[運算子 <](#operator_lt)|測試如果`CSid`物件或`SID`運算子左邊的結構是小於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
|[運算子 >](#operator_gt)|測試如果`CSid`物件或`SID`運算子左邊的結構大於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
|[運算子 < =](#operator_lt__eq)|測試如果`CSid`物件或`SID`運算子左邊的結構是小於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
|[運算子 > =](#operator_gt__eq)|測試如果`CSid`物件或`SID`運算子左邊的結構是大於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsecurity.h。  
  
##  <a name="operator_eq_eq"></a>運算子 = =  
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
 傳回**true**如果物件相等， **false**如果物件不相等。  
  
##  <a name="operator_neq"></a>運算子 ！ =  
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
 傳回**true**物件不相等，如果**false**兩者是否相等。  
  
##  <a name="operator_lt"></a>運算子 <  
 測試如果`CSid`物件或`SID`運算子左邊的結構是小於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>參數  
 `lhs`  
 第一個`CSid`物件或`SID`来比較的結構。  
  
 `rhs`  
 第二個`CSid`物件或`SID`来比較的結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果位址`lhs`物件是否小於的位址`rhs`物件**false**否則。  
  
### <a name="remarks"></a>備註  
 這個運算子是充當的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。  
  
##  <a name="operator_gt"></a>運算子 >  
 測試如果`CSid`物件或`SID`運算子左邊的結構大於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
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
 這個運算子是充當的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。  
  
##  <a name="operator_lt__eq"></a>運算子 < =  
 測試如果`CSid`物件或`SID`運算子左邊的結構是小於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
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
 這個運算子是充當的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。  
  
##  <a name="operator_gt__eq"></a>運算子 > =  
 測試如果`CSid`物件或`SID`運算子左邊的結構是大於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。  
  
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
 這個運算子是充當的位址`CSid`物件或`SID`結構，而且會實作以提供與 c + + 標準程式庫集合類別的相容性。



