---
title: WeakReference 類別 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78b9a62838508c2e97bdd04f56778a622343e6f1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012286"
---
# <a name="weakreference-class1"></a>WeakReference 類別 1
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class WeakReference;  
```  
  
## <a name="remarks"></a>備註  
 代表*弱式參考*可用於使用 Windows 執行階段或傳統 com 使用。 弱式參考代表不一定可存取的物件。  
  
 A **WeakReference**物件會維護*強式參考*，這是物件的指標和*強式參考計數*，這是強的複本數目已藉由散發的參考`Resolve()`方法。 強式參考計數為非零值，而強式參考有效，且該物件是可存取。 當強式參考計數變成零時，強式參考無效，而且該物件是無法存取。  
  
 A **WeakReference**物件一般用來代表其存在由外部執行緒或應用程式所控制的物件。 例如，建構**WeakReference**檔案物件的參考物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。  
  
 **WeakReference**方法都是安全執行緒。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakReference::WeakReference 建構函式](../windows/weakreference-weakreference-constructor.md)|初始化的新執行個體**WeakReference**類別。|  
|[WeakReference::~WeakReference 解構函式](../windows/weakreference-tilde-weakreference-destructor.md)|取消初始化 （終結） 的目前執行個體**WeakReference**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference 方法](../windows/weakreference-decrementstrongreference-method.md)|目前的強式的參考計數的遞減**WeakReference**物件。|  
|[WeakReference::IncrementStrongReference 方法](../windows/weakreference-incrementstrongreference-method.md)|目前的強式參考計數遞增**WeakReference**物件。|  
|[WeakReference::Resolve 方法](../windows/weakreference-resolve-method.md)|如果強式參考計數為非零值，請為目前的強式參考值設定指定的指標。|  
|[WeakReference::SetUnknown 方法](../windows/weakreference-setunknown-method.md)|設定目前的強式參考**WeakReference**物件與指定的介面指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `WeakReference`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)