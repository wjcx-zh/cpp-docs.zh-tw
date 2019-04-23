---
title: vi_progid (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: 7050543c9acf3801a99d3e32e119325900bdb050
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033585"
---
# <a name="viprogid"></a>vi_progid

指定與版本無關的 ProgID 表單。

## <a name="syntax"></a>語法

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>參數

*name*<br/>
版本無關的 ProgID，表示的物件。

Progid 會提供人類看得懂的版本，用來識別的 COM/ActiveX 物件的類別識別項 (CLSID)。

## <a name="remarks"></a>備註

**Vi_progid** C++屬性可讓您指定 COM 物件與版本無關的 ProgID。 ProgID 的形式*name1.name2.version*。 沒有與版本無關的 ProgID*版本*。 可同時指定兩者`progid`而**vi_progid**上的屬性`coclass`。 如果您未指定**vi_progid**，則版本無關的 ProgID 是所指定的值[progid](progid.md)屬性。

**vi_progid**意味著`coclass`屬性，也就是如果您指定**vi_progid**，它是與指定的相同項目`coclass`並**vi_progid**屬性。

**Vi_progid**屬性會導致自動註冊指定的名稱下的類別。 產生的.idl 檔案不會顯示 ProgID 的值。

在 ATL 專案中，如果[coclass](coclass.md)也有屬性時，會使用指定的 ProgID`GetVersionIndependentProgID`函式 (插入`coclass`屬性)。

## <a name="example"></a>範例

請參閱[coclass](coclass.md)的範例使用的範例**vi_progid**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[ProgID 的索引鍵](/windows/desktop/com/-progid--key)
