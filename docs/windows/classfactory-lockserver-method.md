---
title: 'Classfactory:: Lockserver 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee858346fdb70e136edfbc562c2dfffb1f63e462
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652366"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer 方法
遞增或遞減目前所追蹤物件的基礎數目**ClassFactory**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
### <a name="parameters"></a>參數  
 *fLock*  
 **true**遞增追蹤的物件數目。 **false**來減少追蹤的物件數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，E_FAIL。  
  
## <a name="remarks"></a>備註  
 **ClassFactory**追蹤的基礎執行個體中的物件[模組](../windows/module-class.md)類別。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ClassFactory 類別](../windows/classfactory-class.md)