---
title: Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier, constructor
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8e48b6f8ec4a985bfa7fa5b8d0069e472df86e8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605986"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier 建構函式
初始化的新執行個體**module:: methodreleasenotifier**類別。  
  
## <a name="syntax"></a>語法  
  
```  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
### <a name="parameters"></a>參數  
 *object*  
 物件，其成員函式為事件處理常式。  
  
 *方法*  
 成員函式的參數*物件*也就是事件處理常式。  
  
 *release*  
 指定 **，則為 true**若要啟用呼叫基礎[模組:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md)方法; 否則指定**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Module::MethodReleaseNotifier 類別](../windows/module-methodreleasenotifier-class.md)