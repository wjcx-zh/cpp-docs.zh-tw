---
title: 'Module:: releasenotifier 類別 |Microsoft 文件'
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
ms.openlocfilehash: 76edb403fae12dd8b6221d8bd6ec82424bc5a4f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 類別
在模組中的最後一個物件發行時，會叫用事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier 解構函式](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|取消初始化 module:: releasenotifier 類別的目前執行個體。|  
|[Module::ReleaseNotifier::ReleaseNotifier 建構函式](../windows/module-releasenotifier-releasenotifier-constructor.md)|初始化 module:: releasenotifier 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke 方法](../windows/module-releasenotifier-invoke-method.md)|實作時，會發行在模組中的最後一個物件時呼叫的事件處理常式。|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|如果物件以參數的建構，會刪除目前的 module:: releasenotifier 物件`true`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)