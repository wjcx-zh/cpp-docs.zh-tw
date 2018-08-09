---
title: 'Module:: releasenotifier 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97c998f7e0814c5acae55dd3e9b747faed0242e1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016219"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 類別
發行模組中的最後一個物件時，會叫用事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier 解構函式](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|取消初始化目前的執行個體**releasenotifier**類別。|  
|[Module::ReleaseNotifier::ReleaseNotifier 建構函式](../windows/module-releasenotifier-releasenotifier-constructor.md)|初始化的新執行個體**releasenotifier**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke 方法](../windows/module-releasenotifier-invoke-method.md)|實作時，請在發行模組中的最後一個物件時呼叫的事件處理常式。|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|刪除目前**releasenotifier**物件如果物件以參數的建構 **，則為 true**。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)