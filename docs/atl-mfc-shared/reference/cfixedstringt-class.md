---
title: "CFixedStringT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs: C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f66749272649fe230b31e770a175e0b94441b90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 用於固定的字串物件的基底類別，而且可以是任何`CStringT`-基底類型。 一些範例包括`CString`， `CStringA`，和`CStringW`。  
  
 *t_nChars*  
 儲存在緩衝區中的字元數。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|字串物件的建構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|指派新值`CFixedStringT`物件。|  
  
## <a name="remarks"></a>備註  
 這個類別是以基礎的自訂字串類別的範例`CStringT`。 雖然很相似，但兩個類別的不同實作中。 之間的主要差異`CFixedStringT`和`CStringT`是：  
  
-   初始字元緩衝區配置物件的一部分，而且大小*t_nChars*。 這可讓**CFixedString**以佔用連續記憶體區塊 (chunk) 進行效能物件。 不過，如果內容`CFixedStringT`超過下列大小時物件*t_nChars*，緩衝區會以動態方式配置。  
  
-   字元緩衝區`CFixedStringT`物件永遠是相同的長度 ( *t_nChars*)。 上的緩衝區大小沒有限制`CStringT`物件。  
  
-   Memory manager`CFixedStringT`使共用的自訂[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)物件之間的兩部以上`CFixedStringT`objectsis 不允許。 `CStringT`物件不需要這項限制。  
  
 如需有關自訂`CFixedStringT`和字串物件的記憶體管理一般情況下，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>需求  
 **標頭：** cstringt.h  
  
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
 以 null 結束的字串複製到這`CFixedStringT`物件。  
  
 `str`  
 現有`CFixedStringT`物件複製到這個`CFixedStringT`物件。  
  
 `pStringMgr`  
 指向的記憶體管理員的`CFixedStringT`物件。 如需有關`IAtlStringMgr`和記憶體管理`CFixedStringT`，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
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
 以 null 結束的字串複製到這`CFixedStringT`物件。  
  
 `psz`  
 現有`CFixedStringT`複製到這個`CFixedStringT`物件。  
  
### <a name="remarks"></a>備註  
 您應該注意可能發生的例外狀況，每當您使用指派運算子，因為新的存放裝置通常保留所產生的配置該記憶體`CFixedStringT`物件。  
  
## <a name="see-also"></a>請參閱  
 [CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)




