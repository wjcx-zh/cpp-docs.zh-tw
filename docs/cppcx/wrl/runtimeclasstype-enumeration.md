---
title: RuntimeClassType 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
ms.openlocfilehash: 53f0172968c28762bb1305e274bbd47494cdaf4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213573"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType 列舉

指定支援的[RuntimeClass](runtimeclass-class.md)實例類型。

## <a name="syntax"></a>語法

```cpp
enum RuntimeClassType;
```

## <a name="members"></a>成員

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ClassicCom`|傳統 COM 執行時間類別。|
|`Delegate`|相當於 `ClassicCom`。|
|`InhibitFtmBase`|未定義 `__WRL_CONFIGURATION_LEGACY__` 時，停用 `FtmBase` 支援。|
|`InhibitWeakReference`|停用弱式參考支援。|
|`WinRt`|Windows 執行階段類別。|
|`WinRtClassicComMix`|結合 `WinRt` 和 `ClassicCom`。|

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
