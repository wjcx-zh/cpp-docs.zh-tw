---
title: 'Caccessorbase:: Isautoaccessor |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
dev_langs:
- C++
helpviewer_keywords:
- IsAutoAccessor method
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fabf5d182b6fb0eb993300e241ae76e1b61f5cef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="caccessorbaseisautoaccessor"></a>CAccessorBase::IsAutoAccessor
如果資料會自動移動作業期間擷取存取子，則傳回 true。  
  
## <a name="syntax"></a>語法  
  
```cpp
      bool IsAutoAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>參數  
 `nAccessor`  
 [in] 存取子的零位移數字。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**如果存取子是 autoaccessor。 否則會傳回 **false**。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)