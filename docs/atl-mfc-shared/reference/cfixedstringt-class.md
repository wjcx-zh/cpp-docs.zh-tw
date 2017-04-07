---
title: "CFixedStringT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: 17
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f357a70a728b388c3b5d3d26ac4efd0d4c84434a
ms.lasthandoff: 02/24/2017

---
# <a name="cfixedstringt-class"></a>CFixedStringT 類別
此類別代表固定的字元緩衝區的字串物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>參數  
 `StringType`  
 作為固定的字串物件的基底類別，且可以是任何`CStringT`-基礎類型。 部分範例包括`CString`， `CStringA`，和`CStringW`。  
  
 *t_nChars*  
 儲存在緩衝區中的字元數。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|字串物件的建構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|新值指派給`CFixedStringT`物件。|  
  
## <a name="remarks"></a>備註  
 這個類別為基礎的自訂字串類別的範例`CStringT`。 雖然非常類似，但這兩個類別有不同的實作。 之間的主要差異`CFixedStringT`和`CStringT`是︰  
  
-   起始字元緩衝區配置物件的一部分，而且有大小*t_nChars*。 這可讓**CFixedString**佔用連續記憶體區塊，基於效能用途的物件。 不過，如果內容`CFixedStringT`物件超過*t_nChars*，就會以動態方式配置的緩衝區。  
  
-   字元緩衝區`CFixedStringT`物件一律為相同的長度 ( *t_nChars*)。 緩衝區大小不受限制`CStringT`物件。  
  
-   Memory manager`CFixedStringT`可自訂，例如共用[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)物件之間的兩部以上`CFixedStringT`objectsis 不允許。 `CStringT`物件沒有這項限制。  
  
 如需有關自訂`CFixedStringT`和字串物件的記憶體管理的請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>需求  
 **標頭︰** cstringt.h  
  
##  <a name="cfixedstringt"></a>CFixedStringT::CFixedStringT  
 建構 `CFixedStringT` 物件。  
  
```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 以 null 結束字串複製到這`CFixedStringT`物件。  
  
 `str`  
 將現有`CFixedStringT`物件複製到這`CFixedStringT`物件。  
  
 `pStringMgr`  
 指標的記憶體管理員`CFixedStringT`物件。 如需有關`IAtlStringMgr`和記憶體管理`CFixedStringT`，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
### <a name="remarks"></a>備註  
 因為建構函式會將輸入的資料複製到新配置的儲存體，您應該注意可能會造成例外狀況的記憶體。 請注意，某些這些建構函式做為轉換函式。  
  
##  <a name="operator__eq"></a>CFixedStringT::operator =  
 重新初始化現有`CFixedStringT`物件新的資料。  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 以 null 結束字串複製到這`CFixedStringT`物件。  
  
 `psz`  
 將現有`CFixedStringT`複製到這`CFixedStringT`物件。  
  
### <a name="remarks"></a>備註  
 您應該注意可能會發生例外狀況，當您使用指派運算子，因為新的存放裝置通常會配置來保留所產生的記憶體`CFixedStringT`物件。  
  
## <a name="see-also"></a>另請參閱  
 [CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)





