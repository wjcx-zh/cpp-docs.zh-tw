---
title: HString 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eea40f989e7d41afbff2773fcc5e6e5b2cfbafd2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613649"
---
# <a name="hstring-class"></a>HString 類別

來管理使用 RAII 模式的 HSTRING 的存留期的協助程式類別。

## <a name="syntax"></a>語法

```cpp
class HString;
```

## <a name="remarks"></a>備註

Windows 執行階段提供存取權透過 HSTRING 控制代碼的字串。 **HString**類別提供方便函式和運算子，以簡化 HSTRING 控制代碼的使用。 這個類別可以處理您透過使用 RAII 模式，它擁有的 HSTRING 的存留期。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[HString::HString 建構函式](../windows/hstring-hstring-constructor.md)|初始化的新執行個體**HString**類別。|
|[HString::~HString 解構函式](../windows/hstring-tilde-hstring-destructor.md)|終結的目前執行個體**HString**類別。|

### <a name="members"></a>成員

|名稱|描述|
|----------|-----------------|
|[HString::Set 方法](../windows/hstring-set-method.md)|設定目前的值**HString**設為指定的寬字元字串的物件或**HString**參數。|
|[HString::Attach 方法](../windows/hstring-attach-method.md)|將指定**HString**物件與目前**HString**物件。|
|[HString::CopyTo 方法](../windows/hstring-copyto-method.md)|複製目前**HString**到 HSTRING 物件的物件。|
|[HString::Detach 方法](../windows/hstring-detach-method.md)|取消指定的關聯**HString**與其基礎值的物件。|
|[HString::GetAddressOf 方法](../windows/hstring-getaddressof-method.md)|擷取基礎 HSTRING 控制代碼的指標。|
|[HString::Get 方法](../windows/hstring-get-method.md)|擷取基礎 HSTRING 控制代碼的值。|
|[HString::Release 方法](../windows/hstring-release-method.md)|會刪除基礎字串值，並初始化目前**HString**為空值的物件。|
|[HString::MakeReference 方法](../windows/hstring-makereference-method.md)|建立`HStringReference`從指定的字串參數的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[HString::Operator= 運算子](../windows/hstring-operator-assign-operator.md)|將另一個值移**HString**物件與目前**HString**物件。|
|[HString::Operator== 運算子](../windows/hstring-operator-equality-operator.md)|指出兩個參數是否相等。|
|[HString::Operator!= 運算子](../windows/hstring-operator-inequality-operator.md)|表示兩個參數是否不相等。|

## <a name="inheritance-hierarchy"></a>繼承階層

`HString`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)