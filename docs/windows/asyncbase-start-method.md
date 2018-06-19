---
title: 'Asyncbase:: Start 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0acc6f62530daf641a2e4d568ed511d6fd831c20
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860914"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start 方法
啟動非同步作業。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   Start  
)(void);  
```  
  
## <a name="return-value"></a>傳回值  
 S_OK 如果作業開始或已啟動。否則，E_ILLEGAL_STATE_CHANGE。  
  
## <a name="remarks"></a>備註  
 Start （） 是 IAsyncInfo::Start 的預設實作，而且不執行任何實際工作。 若要實際啟動非同步作業，覆寫 onstart （） 的純虛擬方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)