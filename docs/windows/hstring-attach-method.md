---
title: 'Hstring:: Attach 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
dev_langs:
- C++
ms.assetid: 69451979-0014-4959-bc5c-1e4ab6fb28e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8738c44c11c69f8d2479335ce3effc4135dfe0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="hstringattach-method"></a>HString::Attach 方法
將指定的 HString 物件與目前 HString 物件產生關聯。  
  
## <a name="syntax"></a>語法  
  
```  
  
void Attach(  
       HSTRING hstr  
       ) throw()  
```  
  
#### <a name="parameters"></a>參數  
 `hstr`  
 HString 現有的物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)