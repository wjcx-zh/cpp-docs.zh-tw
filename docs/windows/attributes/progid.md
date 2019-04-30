---
title: progid (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 5b0c688ad4d9b607cc1f5fb6b1c6d536a1c7888e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407428"
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

Progid 會提供人類看得懂的版本，用來識別的 COM/ActiveX 物件的類別識別項 (CLSID)。

## <a name="remarks"></a>備註

**Progid** C++屬性可讓您指定 COM 物件的 ProgID。 ProgID 的形式*name1.name2.version*。 如果您未指定*版本*ProgID 的預設版本是 1。 如果您未指定*name1.name2*，預設名稱是*classname.classname*。 如果您未指定**progid**和您指定`vi_progid`， *name1.name2*取自`vi_progid`（下一個循序號碼） 和附加的版本。

如果使用的屬性區塊**progid**也不使用**uuid**，編譯器會檢查登錄，以查看**uuid**存在指定**progid**. 如果**progid**未指定，版本 （和 coclass 的名稱，如果建立在 coclass） 將用來產生**progid**。

**progid**意味著`coclass`屬性，也就是如果您指定**progid**，它是與指定的相同項目`coclass`並**progid**屬性。

**Progid**屬性會導致自動註冊指定的名稱下的類別。 產生的.idl 檔案將不會顯示**progid**值。

使用 ATL 的專案中使用這個屬性時，屬性的行為變更。 除了上述的行為，指定具有此屬性的資訊用於`GetProgID`函式，由插入`coclass`屬性。 如需詳細資訊，請參閱 < [coclass](coclass.md)屬性。

## <a name="example"></a>範例

範例，請參閱[coclass](coclass.md)範例使用**progid**。

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
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[ProgID 的索引鍵](/windows/desktop/com/-progid--key)
