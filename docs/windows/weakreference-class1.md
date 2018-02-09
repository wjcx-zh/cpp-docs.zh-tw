---
title: "WeakReference Class1 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8985434365cb8144fc2ee3680ef19c5b8ed99301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="weakreference-class1"></a>WeakReference Class1
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>備註  
 代表*弱式參考*，可以搭配 Windows 執行階段或傳統 com 使用。 弱式參考代表不一定可存取的物件。  
  
 A`WeakReference`物件會維護*強式參考*，這是物件的指標和*強式參考計數*，這是已藉由散發的強式參考的複本數目Resolve() 方法。 為非零，強式參考計數時，強式參考無效，而且是可存取的物件。 當強式參考計數變成零時，強式參考無效且無法存取的物件。  
  
 WeakReference 物件通常用來代表其存在由外部執行緒或應用程式的物件。 例如，建構 WeakReference 物件從參考檔案物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。  
  
 WeakReference 方法都是安全執行緒。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakReference::WeakReference 建構函式](../windows/weakreference-weakreference-constructor.md)|初始化 WeakReference 類別的新執行個體。|  
|[WeakReference::~WeakReference 解構函式](../windows/weakreference-tilde-weakreference-destructor.md)|取消初始化 （終結） WeakReference 類別的目前執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference 方法](../windows/weakreference-decrementstrongreference-method.md)|將強式參考數目目前 WeakReference 物件。|  
|[WeakReference::IncrementStrongReference 方法](../windows/weakreference-incrementstrongreference-method.md)|目前的 WeakReference 物件的強式參考計數遞增。|  
|[WeakReference::Resolve 方法](../windows/weakreference-resolve-method.md)|如果強式參考計數不是零，則您可以將目前強式參考值的指定的指標。|  
|[WeakReference::SetUnknown 方法](../windows/weakreference-setunknown-method.md)|將目前的 WeakReference 物件的強式參考設定為指定的介面指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `WeakReference`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)