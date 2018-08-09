---
title: Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5aa78562c934c41b2ff2ab7b381f6b2612426651
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014584"
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式
初始化的新執行個體**module:: genericreleasenotifier**類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
### <a name="parameters"></a>參數  
 *回呼*  
 Lambda、 函式或可以使用括號函式運算子叫用的函式指標事件處理常式 (`()`)。  
  
 *release*  
 指定 **，則為 true**若要啟用呼叫基礎[模組:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md)方法; 否則指定**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Module::GenericReleaseNotifier 類別](../windows/module-genericreleasenotifier-class.md)