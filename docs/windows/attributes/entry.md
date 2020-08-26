---
title: '專案 (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 63e5ccebb1d3844af8dd11b4b094abe96e3e257c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845311"
---
# <a name="entry"></a>entry

藉由識別 DLL 中的進入點，在模組中指定匯出的函式或常數。

## <a name="syntax"></a>語法

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>參數

*id*<br/>
進入點的識別碼。

## <a name="remarks"></a>備註

**專案**c + + 屬性的功能與[輸入](/windows/win32/Midl/entry)MIDL 屬性相同。

## <a name="example"></a>範例

如需**進入**範例的範例，請參閱[idl_module](idl-module.md)的範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|`idl_module` 屬性|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)
