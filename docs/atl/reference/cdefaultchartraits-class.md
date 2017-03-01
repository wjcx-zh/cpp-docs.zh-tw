---
title: "CDefaultCharTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATL::CDefaultCharTraits<T>
- ATL.CDefaultCharTraits
- ATL.CDefaultCharTraits<T>
- ATL::CDefaultCharTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
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
ms.openlocfilehash: 12991cfcf1ac96808a0315899d01ce3012324dc6
ms.lasthandoff: 02/24/2017

---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits 類別
這個類別提供兩個靜態函式之間大寫和小寫字元轉換。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T>  
class CDefaultCharTraits
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](#chartolower)|（靜態）呼叫此函式，將字元轉換成大寫。|  
|[CDefaultCharTraits::CharToUpper](#chartoupper)|（靜態）呼叫此函式，將字元轉換成小寫。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供類別所利用的函式[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="a-namechartolowera--cdefaultchartraitschartolower"></a><a name="chartolower"></a>CDefaultCharTraits::CharToLower  
 呼叫此函式，將字元轉換成小寫。  
  
```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```  
  
### <a name="parameters"></a>參數  
 *x*  
 要轉換為小寫的字元。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&132;](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]  
  
##  <a name="a-namechartouppera--cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>CDefaultCharTraits::CharToUpper  
 呼叫此函式，將字元轉換成大寫。  
  
```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```  
  
### <a name="parameters"></a>參數  
 *x*  
 要轉換為大寫的字元。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

