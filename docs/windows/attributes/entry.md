---
title: entry （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 9bdfc64506f26ee4e9876920821883a0fa12bc7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167091"
---
# <a name="entry"></a>項目

藉由識別 DLL 中的進入點，指定模組中匯出的函數或常數。

## <a name="syntax"></a>語法

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>參數

*id*<br/>
進入點的識別碼。

## <a name="remarks"></a>備註

**Entry** C++屬性的功能與[專案](/windows/win32/Midl/entry)MIDL 屬性相同。

## <a name="example"></a>範例

如需使用**專案**的範例，請參閱[idl_module](idl-module.md)的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|`idl_module` 屬性|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)
