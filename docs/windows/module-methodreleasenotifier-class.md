---
title: 'Module:: methodreleasenotifier 類別 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 217e58f73130922d45f0d303e1e91858e8c2272f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 類別
發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-到-a-方法成員所指定的事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 成員函式是事件處理常式的物件類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|初始化 module:: methodreleasenotifier 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke 方法](../windows/module-methodreleasenotifier-invoke-method.md)|呼叫目前 module:: methodreleasenotifier 物件相關聯的事件處理常式。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_ 資料成員](../windows/module-methodreleasenotifier-method-data-member.md)|目前的 module:: methodreleasenotifier 物件的事件處理常式會保留指標。|  
|[Module::MethodReleaseNotifier::object_ 資料成員](../windows/module-methodreleasenotifier-object-data-member.md)|成員函式是目前的 module:: methodreleasenotifier 物件的事件處理常式的物件會保留指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)