---
title: 'SyncLockT:: ~ SyncLockT 解構函式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- ~SyncLockT, destructor
ms.assetid: 9e14870d-017d-45fe-a3dc-cd86b6fa1c3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c91c677a18c66c875107f48c2e04ba45be88fb48
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892731"
---
# <a name="synclocktsynclockt-destructor"></a>SyncLockT::~SyncLockT 解構函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
~SyncLockT();  
```  
  
## <a name="remarks"></a>備註  
 取消初始化 SyncLockT 類別的執行個體。  
  
 此解構函式也會解除鎖定目前 SyncLockT 執行個體。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)