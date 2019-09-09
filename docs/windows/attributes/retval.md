---
title: retval （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 2a2865c1eda229f1a2fcd457c22119b2908c1caa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514055"
---
# <a name="retval"></a>retval

指定接收成員之傳回值的參數。

## <a name="syntax"></a>語法

```cpp
[retval]
```

## <a name="remarks"></a>備註

**Retval** C++屬性的功能與[retval](/windows/win32/Midl/retval) MIDL 屬性相同。

**retval**必須出現在函數的宣告中的最後一個引數上。

## <a name="example"></a>範例

如需使用**retval**的範例，請參閱可系[結的範例](bindable.md)。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數，介面方法|
|**可重複**|否|
|**必要屬性**|**out**|
|**無效屬性**|**in**|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[方法屬性](method-attributes.md)