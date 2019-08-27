---
title: vi_progid (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.vi_progid
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
ms.openlocfilehash: fbf5ab2bc4263356a1cfcf789865a3f7e286ccd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514865"
---
# <a name="vi_progid"></a>vi_progid

指定與版本無關的 ProgID 形式。

## <a name="syntax"></a>語法

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>參數

*name*<br/>
與版本無關的 ProgID, 代表物件。

Progid 呈現了人類看得懂的類別識別碼 (CLSID) 版本, 用來識別 COM/ActiveX 物件。

## <a name="remarks"></a>備註

**Vi_progid** C++屬性可讓您為 COM 物件指定與版本無關的 progid。 ProgID 的格式為*name1*。 與版本無關的 ProgID 沒有*版本*。 您可以在上`progid` `coclass`同時指定和**vi_progid**屬性。 如果您未指定**vi_progid**, 與版本無關的 progid 就是[progid](progid.md)屬性所指定的值。

**vi_progid**意指`coclass`屬性, 也就是說, 如果您指定**vi_progid**, 這與指定`coclass`和**vi_progid**屬性的做法相同。

**Vi_progid**屬性會使類別以指定的名稱自動註冊。 產生的 .idl 檔案不會顯示 ProgID 值。

在 ATL 專案中, 如果[coclass](coclass.md)屬性也存在, 則函式會使用`GetVersionIndependentProgID`指定的 ProgID `coclass` (由屬性插入)。

## <a name="example"></a>範例

如需使用**vi_progid**的範例, 請參閱[coclass](coclass.md)範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[ProgID 金鑰](/windows/win32/com/-progid--key)
