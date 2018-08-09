---
title: SyncLockT 類別 |Microsoft Docs
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
ms.openlocfilehash: b1eb11480657d731a4667722572e921f405c0845
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012140"
---
# <a name="synclockt-class"></a>SyncLockT 類別
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
### <a name="parameters"></a>參數  
 *SyncTraits*  
 可以取得資源的擁有權類型。  
  
## <a name="remarks"></a>備註  
 代表一種類型，可以採取獨佔或共用資源的擁有權。  
  
 **SyncLockT**會使用類別，例如，以協助實作[SRWLock](../windows/srwlock-class.md)類別。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 建構函式](../windows/synclockt-synclockt-constructor.md)|初始化的新執行個體**SyncLockT**類別。|  
|[SyncLockT::~SyncLockT 解構函式](../windows/synclockt-tilde-synclockt-destructor.md)|取消初始化的執行個體**SyncLockT**類別。|  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::SyncLockT 建構函式](../windows/synclockt-synclockt-constructor.md)|初始化的新執行個體**SyncLockT**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::IsLocked 方法](../windows/synclockt-islocked-method.md)|指出是否目前**SyncLockT**物件擁有資源，也就是，則**SyncLockT**物件*鎖定*。|  
|[SyncLockT::Unlock 方法](../windows/synclockt-unlock-method.md)|目前所持有的資源的控制權**SyncLockT**物件，如果有的話。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[SyncLockT::sync_ 資料成員](../windows/synclockt-sync-data-member.md)|表示的基礎資源會保留**SyncLockT**類別。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SyncLockT`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock 類別](../windows/srwlock-class.md)