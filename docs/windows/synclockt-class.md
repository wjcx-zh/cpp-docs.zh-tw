---
title: SyncLockT 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e05a1be5d84db52573d3c3235936ecf82dde5894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="synclockt-class"></a>SyncLockT 類別
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### <a name="parameters"></a>參數  
 `SyncTraits`  
 可取得資源的擁有權類型。  
  
## <a name="remarks"></a>備註  
 代表類型可取用獨佔或共用資源的擁有權。  
  
 SyncLockT 類別使用，例如，以協助實作[SRWLock](../windows/srwlock-class.md)類別。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 建構函式](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 類別的新執行個體。|  
|[SyncLockT::~SyncLockT 解構函式](../windows/synclockt-tilde-synclockt-destructor.md)|取消初始化 SyncLockT 類別的執行個體。|  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 建構函式](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::IsLocked 方法](../windows/synclockt-islocked-method.md)|指出目前的 SyncLockT 物件是否擁有資源;也就是說，SyncLockT 物件是*鎖定*。|  
|[SyncLockT::Unlock 方法](../windows/synclockt-unlock-method.md)|釋放目前 SyncLockT 物件所持有的資源的控制，如果有的話。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::sync_ 資料成員](../windows/synclockt-sync-data-member.md)|保存 SyncLockT 類別所代表的基礎資源。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SyncLockT`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock 類別](../windows/srwlock-class.md)