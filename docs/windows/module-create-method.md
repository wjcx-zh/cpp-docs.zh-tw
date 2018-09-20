---
title: 'Module:: create 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8b84bcaec7dbadfb7b735264df12f7e958dcd20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444693"
---
# <a name="modulecreate-method"></a>Module::Create 方法

建立模組的執行個體。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()  
);
```

### <a name="parameters"></a>參數

*T*<br/>
模組類型。

*回呼*<br/>
當您釋放最後一個執行個體物件的模組時呼叫。

*object*<br/>
*物件*並*方法*參數搭配使用的。 點的最後一個執行個體物件，當使用者放開模組中的最後一個執行個體物件。

*方法*<br/>
*物件*並*方法*參數搭配使用的。 方法的最後一個執行個體物件時釋放最後一個執行個體物件模組中的點。

## <a name="return-value"></a>傳回值

模組參考。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Module 類別](../windows/module-class.md)