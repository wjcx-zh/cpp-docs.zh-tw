---
title: '執行緒 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: 6f83dca442b6508207a4123fa918fc5078bdf664
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840813"
---
# <a name="threading-c"></a>threading (C++)

指定 COM 物件的執行緒模型。

## <a name="syntax"></a>語法

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>參數

*model*<br/>
 (選擇性) 下列其中一個執行緒模型：

- `apartment` (的單元執行緒) 

- `neutral` ( 沒有使用者介面的 .NET Framework 元件) 

- `single` (簡單的執行緒) 

- `free` (自由執行緒) 

- `both` (的單元和自由執行緒) 

預設值是 `apartment`。

## <a name="remarks"></a>備註

**執行緒**c + + 屬性不會出現在產生的 .idl 檔案中，但將用於您的 COM 物件的執行。

在 ATL 專案中，如果 [coclass](coclass.md) 屬性也存在， *模型* 所指定的執行緒模型會以樣板參數的形式傳遞至 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 類別，並由屬性插入 `coclass` 。

**執行緒**屬性也會保護[event_source](event-source.md)的存取。

## <a name="example"></a>範例

請參閱 [授權](licensed.md) 範例以取得 **執行緒**的範例使用。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[舊版程式碼的多執行緒支援 (Visual C++) ](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[中性單元](/windows/win32/cossdk/neutral-apartments)
