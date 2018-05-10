---
title: ComPtrRef 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d961ed0a675927846788c013e61767f99b408c6b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="comptrref-class"></a>ComPtrRef 類別
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md)型別或型別衍生自它不只是 ComPtr 所代表的介面。  
  
## <a name="remarks"></a>備註  
 表示 ComPtr 類型的物件參考\<T >。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtrRef::ComPtrRef 建構函式](../windows/comptrref-comptrref-constructor.md)|初始化指定的指標到另一個的 ComPtrRef 物件的 ComPtrRef 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtrRef::GetAddressOf 方法](../windows/comptrref-getaddressof-method.md)|擷取目前的 ComPtrRef 物件所代表之介面的指標位址。|  
|[ComPtrRef::ReleaseAndGetAddressOf 方法](../windows/comptrref-releaseandgetaddressof-method.md)|刪除目前的 ComPtrRef 物件，並傳回已 ComPtrRef 物件所代表的介面指標至 a 的指標。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtrRef::operator InterfaceType** 運算子](../windows/comptrref-operator-interfacetype-star-star-operator.md)|刪除目前的 ComPtrRef 物件，並傳回已 ComPtrRef 物件所代表的介面指標至 a 的指標。|  
|[ComPtrRef::operator T* 運算子](../windows/comptrref-operator-t-star-operator.md)|傳回的值[ptr_](../windows/comptrrefbase-ptr-data-member.md)目前 ComPtrRef 物件的資料成員。|  
|[ComPtrRef::operator void** 運算子](../windows/comptrref-operator-void-star-star-operator.md)|刪除目前的 ComPtrRef 物件，會轉換至已做為指標--指標-將 ComPtrRef 物件所代表的介面指標`void`，然後傳回轉型指標。|  
|[ComPtrRef::operator* 運算子](../windows/comptrref-operator-star-operator.md)|擷取目前的 ComPtrRef 物件所代表之介面指標。|  
|[ComPtrRef::operator== 運算子](../windows/comptrref-operator-equality-operator.md)|指出兩個 ComPtrRef 物件是否相等。|  
|[ComPtrRef::operator!= 運算子](../windows/comptrref-operator-inequality-operator.md)|指出兩個 ComPtrRef 物件是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)