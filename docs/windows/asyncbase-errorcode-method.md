---
title: 'Asyncbase:: Errorcode 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abd3eae18d793739866b6c0dd8a1b6a994093c93
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859575"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode 方法
擷取目前的非同步作業的錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
#### <a name="parameters"></a>參數  
 `error`  
 這項作業對目前的錯誤程式碼的儲存位置。  
  
## <a name="remarks"></a>備註  
 這項作業是安全執行緒。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)