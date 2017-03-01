---
title: "CAtlFileMapping 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlFileMapping<T>
- ATL.CAtlFileMapping
- ATL::CAtlFileMapping
- CAtlFileMapping
- ATL.CAtlFileMapping<T>
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: 20
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
ms.openlocfilehash: 2693647af904eab1ed0f84bc406bc1207d4a9b8c
ms.lasthandoff: 02/24/2017

---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 類別
此類別代表記憶體對應檔案，加入方法的轉換運算子[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 用於轉換運算子的資料型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|允許隱含轉換的`CAtlFileMapping`物件加入至`T` ** \* **。|  
  
## <a name="remarks"></a>備註  
 這個類別會加入單一的轉換運算子，以允許隱含轉換`CAtlFileMapping`物件加入至`T` ** \* **。 由基底類別，提供其他成員[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlfile.h  
  
##  <a name="a-nameoperatortstara--catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::operator T *  
 允許隱含轉換的`CAtlFileMapping`物件加入至`T` ** \* **。  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`T` ** \* **於記憶體對應檔的開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata)轉換為傳回的指標和`T` ** \* **其中*T*是做為這個類別的範本參數的型別。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlFileMappingBase 類別](../../atl/reference/catlfilemappingbase-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

