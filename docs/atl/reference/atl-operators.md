---
title: ATL 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5027fa4b84d84bf07766c7ac4e75f140706f0c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103699"
---
# <a name="atl-operators"></a>ATL 運算子

此章節包含 ATL 全域運算子參考主題。

|運算子|描述|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|比較兩個`CSid`物件或`SID`結構是否相等。|
|[運算子 ！ =](#operator_neq)|比較兩個`CSid`物件或`SID`結構是否不相等。|
|[運算子 <](#operator_lt)|測試是否`CSid`物件或`SID`運算子左邊的結構是否小於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|
|[運算子 >](#operator_gt)|測試是否`CSid`物件或`SID`運算子左邊的結構是否大於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|
|[運算子 < =](#operator_lt__eq)|測試是否`CSid`物件或`SID`運算子左邊的結構是否小於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|
|[運算子 > =](#operator_gt__eq)|測試是否`CSid`物件或`SID`運算子左邊的結構是否大於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。|

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h。

##  <a name="operator_eq_eq"></a>  運算子 = =

比較`CSid`物件或`SID`結構是否相等的 （安全性識別碼）。

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*  
第一個`CSid`物件或`SID`来比較的結構。

*rhs*  
第二個`CSid`物件或`SID`来比較的結構。

### <a name="return-value"></a>傳回值

為 true，則傳回的物件是否相等，FALSE 如果不相等。

##  <a name="operator_neq"></a>  運算子 ！ =

比較`CSid`物件或`SID`結構是否不相等的 （安全性識別碼）。

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*  
第一個`CSid`物件或`SID`来比較的結構。

*rhs*  
第二個`CSid`物件或`SID`来比較的結構。

### <a name="return-value"></a>傳回值

為 true，則傳回的物件是否不相等，如果相等，則為 FALSE。

##  <a name="operator_lt"></a>  運算子 <

測試是否`CSid`物件或`SID`運算子左邊的結構是否小於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*  
第一個`CSid`物件或`SID`来比較的結構。

*rhs*  
第二個`CSid`物件或`SID`来比較的結構。

### <a name="return-value"></a>傳回值

如果為 true 的地址*lhs*物件是否小於一個的位址*rhs*物件，FALSE 否則。

### <a name="remarks"></a>備註

此運算子處理程式碼的地址`CSid`物件或`SID`結構，並實作以提供與 c + + 標準程式庫集合類別的相容性。

##  <a name="operator_gt"></a>  運算子 >

測試是否`CSid`物件或`SID`運算子左邊的結構是否大於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*  
第一個`CSid`物件或`SID`来比較的結構。

*rhs*  
第二個`CSid`物件或`SID`来比較的結構。

### <a name="return-value"></a>傳回值

如果為 true 的地址*lhs*大於的地址*rhs*，否則為 FALSE 否則。

### <a name="remarks"></a>備註

此運算子處理程式碼的地址`CSid`物件或`SID`結構，並實作以提供與 c + + 標準程式庫集合類別的相容性。

##  <a name="operator_lt__eq"></a>  運算子 < =

測試是否`CSid`物件或`SID`運算子左邊的結構是否小於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*  
第一個`CSid`物件或`SID`来比較的結構。

*rhs*  
第二個`CSid`物件或`SID`来比較的結構。

### <a name="return-value"></a>傳回值

如果為 true 的地址*lhs*小於或等於的地址*rhs*，否則為 FALSE 否則。

### <a name="remarks"></a>備註

此運算子處理程式碼的地址`CSid`物件或`SID`結構，並實作以提供與 c + + 標準程式庫集合類別的相容性。

##  <a name="operator_gt__eq"></a>  運算子 > =

測試是否`CSid`物件或`SID`運算子左邊的結構是否大於或等於`CSid`物件或`SID`（適用於 c + + 標準程式庫相容性） 右側的結構。

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*  
第一個`CSid`物件或`SID`来比較的結構。

*rhs*  
第二個`CSid`物件或`SID`来比較的結構。

### <a name="return-value"></a>傳回值

如果為 true 的地址*lhs*大於或等於的地址*rhs*，否則為 FALSE 否則。

### <a name="remarks"></a>備註

此運算子處理程式碼的地址`CSid`物件或`SID`結構，並實作以提供與 c + + 標準程式庫集合類別的相容性。

