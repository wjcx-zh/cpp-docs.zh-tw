---
title: 項目 (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 703a55ee7c56b64a5b168016770508508bab09e0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036298"
---
# <a name="entry"></a>entry

指定匯出的函式或常數 」 模組中，找出 DLL 的進入點。

## <a name="syntax"></a>語法

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>參數

*id*<br/>
進入點的識別碼。

## <a name="remarks"></a>備註

**項目**C++屬性具有相同的功能[項目](/windows/desktop/Midl/entry)MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[idl_module](idl-module.md)範例使用**項目**。

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