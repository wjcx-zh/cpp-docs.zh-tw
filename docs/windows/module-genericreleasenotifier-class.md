---
title: 'Module:: genericreleasenotifier 類別 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3ba58e08bac36d905fbf874546d7791f2aa3fcb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier 類別
發行目前的模組中的最後一個物件時，會叫用事件處理常式。 Lambda、 函式或函式指標上所指定的事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 包含此事件處理常式位置的資料成員型別。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|初始化 module:: genericreleasenotifier 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke 方法](../windows/module-genericreleasenotifier-invoke-method.md)|呼叫目前 module:: genericreleasenotifier 物件相關聯的事件處理常式。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_ 資料成員](../windows/module-genericreleasenotifier-callback-data-member.md)|保存 lambda、 函式或與目前的 module:: genericreleasenotifier 物件相關聯的函式指標事件處理常式。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)