---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: ed4950b9e90ef968fcf0c42e4f0a9775c58ea7ec
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030163"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**C++ 專有的**

不為類型程式庫中的所有介面建立智慧型指標。

## <a name="syntax"></a>語法

```
no_smart_pointers
```

## <a name="remarks"></a>備註

根據預設，當您使用 `#import` 時，會得到類型程式庫中所有介面的智慧型指標宣告。 這些智慧型指標的類型是[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)。

**END C++ 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)