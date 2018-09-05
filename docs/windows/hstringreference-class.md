---
title: HStringReference 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b80ae92671b2ee78cd2f48e9a35958c89232e4e5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683037"
---
# <a name="hstringreference-class"></a>HStringReference 類別

表示從現有字串建立的 HSTRING。

## <a name="syntax"></a>語法

```cpp
class HStringReference;
```

## <a name="remarks"></a>備註

新的 HSTRING 中支援緩衝區的存留期不受 Windows 執行階段。 呼叫端配置來源字串上的堆疊框架，以避免堆積配置，並排除記憶體流失的風險。 此外，呼叫端必須確保來源字串附加的 HSTRING 的存留期間會保持不變。 如需詳細資訊，請參閱 < [WindowsCreateStringReference 函式](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[HStringReference::HStringReference 建構函式](../windows/hstringreference-hstringreference-constructor.md)|初始化的新執行個體**HStringReference**類別。|

### <a name="members"></a>成員

|成員|描述|
|------------|-----------------|
|[HStringReference::CopyTo 方法](../windows/hstringreference-copyto-method.md)|複製目前**HStringReference**到 HSTRING 物件的物件。|
|[HStringReference::Get 方法](../windows/hstringreference-get-method.md)|擷取基礎 HSTRING 控制代碼的值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[HStringReference::Operator= 運算子](../windows/hstringreference-operator-assign-operator.md)|將另一個值移**HStringReference**物件與目前**HStringReference**物件。|
|[HStringReference::Operator== 運算子](../windows/hstringreference-operator-equality-operator.md)|指出兩個參數是否相等。|
|[HStringReference::Operator!= 運算子](../windows/hstringreference-operator-inequality-operator.md)|表示兩個參數是否不相等。|

## <a name="inheritance-hierarchy"></a>繼承階層

`HStringReference`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)