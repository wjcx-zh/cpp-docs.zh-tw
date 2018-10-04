---
title: retval （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2b71271dc0579e1d0682b95a0d3bdf57d197d1a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790943"
---
# <a name="retval"></a>retval

指定接收成員的傳回值的參數。

## <a name="syntax"></a>語法

```cpp
[retval]
```

## <a name="remarks"></a>備註

**Retval** c + + 屬性具有相同的功能[retval](/windows/desktop/Midl/retval) MIDL 屬性。

**retval**必須出現在函式宣告中的最後一個引數。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**retval**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，介面方法|
|**可重複**|否|
|**必要屬性**|**out**|
|**無效屬性**|**in**|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)  