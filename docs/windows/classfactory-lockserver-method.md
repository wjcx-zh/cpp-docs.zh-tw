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
ms.openlocfilehash: 654ef60c924a14e861971c651899c8baea0300ef
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462702"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer 方法
遞增或遞減目前所追蹤物件的基礎數目**ClassFactory**物件。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>參數  
 *fLock*  
 **true**遞增追蹤的物件數目。 **false**來減少追蹤的物件數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，E_FAIL。  
  
## <a name="remarks"></a>備註  
 ClassFactory 會持續追蹤的基礎執行個體中的物件[模組](../windows/module-class.md)類別。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ClassFactory 類別](../windows/classfactory-class.md)