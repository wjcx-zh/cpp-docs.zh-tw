---
title: Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式 |Microsoft 文件
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
ms.openlocfilehash: bb07c7f53e27e380ba5775369611299cad0f60d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875054"
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier 建構函式
初始化 module:: genericreleasenotifier 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
      GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### <a name="parameters"></a>參數  
 `callback`  
 Lambda、 函式或可以用來叫用括號函式運算子的函式指標事件處理常式 (`()`)。  
  
 `release`  
 指定`true`啟用呼叫基礎[模組:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md)方法; 否則指定`false`。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Module::GenericReleaseNotifier 類別](../windows/module-genericreleasenotifier-class.md)