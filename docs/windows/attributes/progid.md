---
title: 'progid (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 136c651ec92c78339c2f701804a6a409523dd30f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839994"
---
# <a name="progid"></a>progid

指定 COM 物件的 ProgID。

## <a name="syntax"></a>語法

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>參數

*name*<br/>
代表物件的 ProgID。

Progid 會提供人們可讀取的類別識別碼版本 (CLSID) 用來識別 COM/ActiveX 物件。

## <a name="remarks"></a>備註

`progid`C + + 屬性可讓您指定 COM 物件的 ProgID。 ProgID 的格式為 *name1*。 如果您未指定 ProgID 的 *版本* ，預設版本為1。 如果您未指定 *name1*，預設名稱為 *classname.* 類別名稱。 如果您未指定 `progid` ，而且您指定了 `vi_progid` ，則會從 *name1* 取得， `vi_progid` 並附加 (下一個序號) 版本。

如果使用的屬性區塊 `progid` 也不使用 `uuid` ，則編譯器會檢查登錄，以查看是否有指定的 `uuid` `progid` 。 如果 `progid` 未指定，則會使用版本 (和 coclass 名稱，如果建立 coclass) 將會用來產生 `progid` 。

`progid` 意指屬性，亦即， `coclass` 如果您指定 `progid` ，就會與指定和屬性的做法相同 `coclass` `progid` 。

`progid`屬性會讓類別在指定的名稱下自動註冊。 產生的 .idl 檔將不會顯示 `progid` 值。

當這個屬性用於使用 ATL 的專案內時，屬性的行為會變更。 除了上述行為之外，使用這個屬性指定的資訊會在函式中使用 `GetProgID` ，並由屬性插入 `coclass` 。 如需詳細資訊，請參閱 [coclass](coclass.md) 屬性。

## <a name="example"></a>範例

如需的範例用法，請參閱 [coclass](coclass.md) 的範例 `progid` 。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|`class`, `struct`|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID 索引鍵](/windows/win32/com/-progid--key)
