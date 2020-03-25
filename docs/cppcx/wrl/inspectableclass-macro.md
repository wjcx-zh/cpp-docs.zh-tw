---
title: InspectableClass 巨集
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 755a8f58ffc290d73d6060b0b0924905ecbf6028
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213872"
---
# <a name="inspectableclass-macro"></a>InspectableClass 巨集

設定執行時間類別名稱和信任層級。

## <a name="syntax"></a>語法

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>參數

*runtimeClassName*<br/>
執行時間類別的完整文字名稱。

*trustLevel*<br/>
其中一個[TrustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel)列舉值。

## <a name="remarks"></a>備註

**InspectableClass**宏只能搭配 Windows 執行階段類型使用。

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[RuntimeClass 類別](runtimeclass-class.md)
