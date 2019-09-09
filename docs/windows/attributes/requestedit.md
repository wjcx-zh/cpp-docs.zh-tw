---
title: requestedit （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requestedit
helpviewer_keywords:
- requestedit attribute
ms.assetid: b3c24790-3c4a-4646-8722-03d7b51172ee
ms.openlocfilehash: e90506619d4f13d4e5627f9c06b997d7034b5f49
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514086"
---
# <a name="requestedit"></a>requestedit

表示屬性支援 `OnRequestEdit` 通知。

## <a name="syntax"></a>語法

```cpp
[requestedit]
```

## <a name="remarks"></a>備註

**Requestedit** C++屬性具有與[requestedit](/windows/win32/Midl/requestedit) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需**requestedit**的範例用法，請參閱可系[結的範例](bindable.md)。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[資料成員屬性](data-member-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)