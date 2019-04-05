---
title: 說明檔案 （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 7aff6addffb13d2d45953d190eeaac518fe48d6d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039290"
---
# <a name="helpfile"></a>helpfile

設定型別程式庫的說明檔的名稱。

## <a name="syntax"></a>語法

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>參數

*filename*<br/>
包含 [說明] 主題的檔案名稱。

## <a name="remarks"></a>備註

**Helpfile** c + + 屬性具有相同的功能[helpfile](/windows/desktop/Midl/helpfile) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[模組](module-cpp.md)如需如何使用的範例**helpfile**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**， **typedef**，**類別**，方法中，**屬性**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)