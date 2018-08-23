---
title: 'Comptr:: Comptr 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae03de851d7cf24d7322ff6f9e1f8610a584b376
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606212"
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr 建構函式

初始化的新執行個體**ComPtr**類別。 多載提供預設、複製、移動和轉換建構函式。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW ComPtr();
WRL_NOTHROW ComPtr(
   decltype(__nullptr)  
);
template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr(
   const ComPtr& other
);
template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>參數

*U*  
型別*其他*參數。

*other*  
型別的物件*U*。

## <a name="return-value"></a>傳回值

## <a name="remarks"></a>備註

第一個建構函式是預設建構函式，哪一個隱含建立空的物件。 第二個建構函式指定[__nullptr](../windows/nullptr-cpp-component-extensions.md)，明確建立空的物件。

第三個建構函式會從指標所指定的物件建立的物件。

第四個和第五個建構函式是複製建構函式。 第五個建構函式將物件複製時轉換成目前的類型。

第六個和第七個建構函式會移動建構函式。 第七個建構函式會移動物件，如果它是可以轉換成目前的類型。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ComPtr 類別](../windows/comptr-class.md)