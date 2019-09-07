---
title: default 命名空間
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: b67aedc791ed41e93268d9e9f44492781940d55e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740508"
---
# <a name="default-namespace"></a>default 命名空間

命名空間會涵蓋C++/cx。支援的內建類型。 `default`

## <a name="syntax"></a>語法

```
namespace default;
```

### <a name="members"></a>成員

所有內建類型都會繼承下列成員。

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|判斷指定的物件是否等於目前的物件。|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|傳回這個執行個體的雜湊碼。|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|傳回字串，表示目前的類型。|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|傳回字串，表示目前的類型。|

### <a name="built-in-types"></a>內建類型

|名稱|描述|
|----------|-----------------|
|`char16`|表示 Unicode (UTF-16) 字碼指標的 16 位元非數值。|
|`float32`|32 位元 IEEE 754 浮點數。|
|`float64`|64 位元 IEEE 754 浮點數。|
|`int16`|16 位元帶正負號的整數。|
|`int32`|32 位元帶正負號的整數。|
|`int64`|64 位元帶正負號的整數。|
|`int8`|8 位元帶正負號的數值。|
|`uint16`|16 位元不帶正負號的整數。|
|`uint32`|32 位元不帶正負號的整數。|
|`uint64`|64 位元不帶正負號的整數。|
|`uint8`|8 位元不帶正負號的數值。|

### <a name="requirements"></a>需求

**標頭：** vccorlib.h

## <a name="see-also"></a>另請參閱

[C++/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)
