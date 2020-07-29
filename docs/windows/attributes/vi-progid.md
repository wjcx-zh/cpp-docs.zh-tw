---
title: vi_progid （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: e7da3463b142fbca83387e52394ee33f42636124
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213784"
---
# <a name="vi_progid"></a>vi_progid

指定與版本無關的 ProgID 形式。

## <a name="syntax"></a>語法

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>參數

*name*<br/>
與版本無關的 ProgID，代表物件。

Progid 呈現了人類看得懂的類別識別碼（CLSID）版本，用來識別 COM/ActiveX 物件。

## <a name="remarks"></a>備註

**Vi_progid** c + + 屬性可讓您為 COM 物件指定與版本無關的 progid。 ProgID 的格式為*name1*。 與版本無關的 ProgID 沒有*版本*。 您可以 `progid` 在上同時指定和**vi_progid**屬性 `coclass` 。 如果您未指定**vi_progid**，與版本無關的 progid 就是[progid](progid.md)屬性所指定的值。

**vi_progid**意指 `coclass` 屬性，也就是說，如果您指定**vi_progid**，這就是指定 `coclass` 和**vi_progid**屬性的相同做法。

**Vi_progid**屬性會導致類別在指定的名稱下自動註冊。 產生的 .idl 檔案不會顯示 ProgID 值。

在 ATL 專案中，如果[coclass](coclass.md)屬性也存在，則函式會使用指定的 ProgID `GetVersionIndependentProgID` （由 `coclass` 屬性插入）。

## <a name="example"></a>範例

如需**vi_progid**用法的範例，請參閱[coclass](coclass.md)範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[ProgID 金鑰](/windows/win32/com/-progid--key)
