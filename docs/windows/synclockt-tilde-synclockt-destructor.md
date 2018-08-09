---
title: 'SyncLockT:: ~ SyncLockT 解構函式 |Microsoft Docs'
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
ms.openlocfilehash: 85ff68b4a3739c9a258e8664f261c61bb47971db
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018516"
---
# <a name="synclocktsynclockt-destructor"></a>SyncLockT::~SyncLockT 解構函式
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
~SyncLockT();  
```  
  
## <a name="remarks"></a>備註  
 取消初始化的執行個體**SyncLockT**類別。  
  
 此解構函式也會解除鎖定的目前**SyncLockT**執行個體。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)