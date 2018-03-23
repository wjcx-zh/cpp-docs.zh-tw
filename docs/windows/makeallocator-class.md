---
title: MakeAllocator 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33ba172099fd2554709cc539eeee8999c0e42cef
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="makeallocator-class"></a>MakeAllocator 類別
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>, T)>
 class MakeAllocator;  
  
template<typename T>  
class MakeAllocator<T, false>;  
  
template<typename T>  
class MakeAllocator<T, true>;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類型名稱。  
  
 `hasWeakReferenceSupport`  
 `true` 為支援弱式參考; 的物件配置記憶體`false`不支援弱式參考的物件配置記憶體。  
  
## <a name="remarks"></a>備註  
 可啟用類別，或不支援弱式參考，會配置記憶體。  
  
 MakeAllocator 類別來實作使用者定義的記憶體配置模型來覆寫。  
  
 MakeAllocator 通常用來避免記憶體流失，如果在建構期間擲回的物件。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[MakeAllocator::MakeAllocator 建構函式](../windows/makeallocator-makeallocator-constructor.md)|初始化 MakeAllocator 類別的新執行個體。|  
|[MakeAllocator::~MakeAllocator 解構函式](../windows/makeallocator-tilde-makeallocator-destructor.md)|取消初始化 MakeAllocator 類別的目前執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[MakeAllocator::Allocate 方法](../windows/makeallocator-allocate-method.md)|配置記憶體，並將它與目前 MakeAllocator 物件產生關聯。|  
|[MakeAllocator::Detach 方法](../windows/makeallocator-detach-method.md)|取消關聯所配置的記憶體[配置](../windows/makeallocator-allocate-method.md)從目前 MakeAllocator 物件的方法。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `MakeAllocator`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)