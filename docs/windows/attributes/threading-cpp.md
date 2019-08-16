---
title: 執行緒 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: db2940ec3536ae8ea29ba40db84ea869ecb3d0ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513926"
---
# <a name="threading-c"></a>threading (C++)

指定 COM 物件的執行緒模型。

## <a name="syntax"></a>語法

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>參數

*model*<br/>
選擇性下列其中一個執行緒模型:

- `apartment`(公寓執行緒)

- `neutral`(不含使用者介面的 .NET Framework 元件)

- `single`(簡單線程)

- `free`(自由執行緒)

- `both`(公寓和自由執行緒)

預設值為 `apartment`。

## <a name="remarks"></a>備註

**執行緒** C++屬性不會出現在產生的 .idl 檔案中, 但是會用於 COM 物件的執行。

在 ATL 專案中, 如果[coclass](coclass.md)屬性也存在, *model*所指定的執行緒模型就會當做樣板參數傳遞至[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) `coclass`類別, 並由屬性插入。

**執行緒**屬性也會保護對[event_source](event-source.md)的存取。

## <a name="example"></a>範例

如需使用**執行緒**的範例, 請參閱[授權](licensed.md)的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[舊版程式碼的多執行緒支援 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[中性單元](/windows/win32/cossdk/neutral-apartments)