---
title: helpfile |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66cd89c28ea01c3a75d0cb25aa6f96a234e379b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418199"
---
# <a name="helpfile"></a>helpfile

設定型別程式庫的說明檔的名稱。

## <a name="syntax"></a>語法

```cpp
[ helpfile(
   "filename"
) ]
```

### <a name="parameters"></a>參數

*filename*<br/>
包含 [說明] 主題的檔案名稱。

## <a name="remarks"></a>備註

**Helpfile** c + + 屬性具有相同的功能[helpfile](/windows/desktop/Midl/helpfile) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[模組](../windows/module-cpp.md)如需如何使用的範例**helpfile**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**， **typedef**，**類別**，方法中，**屬性**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)<br/>
[介面屬性](../windows/interface-attributes.md)<br/>
[類別屬性](../windows/class-attributes.md)<br/>
[方法屬性](../windows/method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](../windows/helpcontext.md)<br/>
[helpstring](../windows/helpstring.md)  