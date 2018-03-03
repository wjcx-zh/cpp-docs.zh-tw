---
title: "HandleT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ff7261735149abb8db607c5fc0cd4aa837fdfd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="handlet-class"></a>HandleT 類別
物件，表示控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### <a name="parameters"></a>參數  
 `HandleTraits`  
 執行個體[HandleTraits](../windows/handletraits-structure.md) stucture 定義的控制代碼的一般特性。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`Traits`|`HandleTraits` 的同義字。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[HandleT::HandleT 建構函式](../windows/handlet-handlet-constructor.md)|初始化 HandleT 類別的新執行個體。|  
|[HandleT::~HandleT 解構函式](../windows/handlet-tilde-handlet-destructor.md)|取消初始化 HandleT 類別的執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[HandleT::Attach 方法](../windows/handlet-attach-method.md)|將指定的控制代碼與目前 HandleT 物件產生關聯。|  
|[HandleT::Close 方法](../windows/handlet-close-method.md)|關閉目前的 HandleT 物件。|  
|[HandleT::Detach 方法](../windows/handlet-detach-method.md)|取消目前 HandleT 物件從其基礎控制代碼的關聯。|  
|[HandleT::Get 方法](../windows/handlet-get-method.md)|取得基礎控制代碼的值。|  
|[HandleT::IsValid 方法](../windows/handlet-isvalid-method.md)|指出目前的 HandleT 物件是否表示控制代碼。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[HandleT::InternalClose 方法](../windows/handlet-internalclose-method.md)|關閉目前的 HandleT 物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[HandleT::operator= 運算子](../windows/handlet-operator-assign-operator.md)|將指定之 HandleT 物件的值移至目前 HandleT 物件。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[HandleT::handle_ 資料成員](../windows/handlet-handle-data-member.md)|包含 HandleT 物件所代表的控制代碼。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `HandleT`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)