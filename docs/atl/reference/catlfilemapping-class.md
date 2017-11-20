---
title: "CAtlFileMapping 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs: C++
helpviewer_keywords: CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a028c2458b0a5085a1f46bf31f377e6ed9e4d346
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 類別
此類別代表記憶體對應檔案，加入的方法中的轉換運算子[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 用於轉換運算子的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|允許的隱含轉換`CAtlFileMapping`物件加入至`T`  **\*** 。|  
  
## <a name="remarks"></a>備註  
 這個類別會加入單一轉換運算子隱含轉換，以便`CAtlFileMapping`物件加入至`T`  **\*** 。 由基底類別，提供其他成員[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlfile.h  
  
##  <a name="operator_t_star"></a>CAtlFileMapping::operator T *  
 允許的隱含轉換`CAtlFileMapping`物件加入至`T`  **\*** 。  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`T`  **\*** 之記憶體對應檔的開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata)和轉換做為傳回的指標`T`  **\*** 其中*T*是做為範本的類型這個類別的參數。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlFileMappingBase 類別](../../atl/reference/catlfilemappingbase-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
