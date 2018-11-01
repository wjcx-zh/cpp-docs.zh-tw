---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 202d5b23a5e2e8e673e3c220b9618cfe6cd4f0d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525602"
---
# <a name="embeddedidl"></a>embedded_idl

**C + + 特定**

指定類型程式庫將寫入 .tlh 檔，並保留屬性產生的程式碼。

## <a name="syntax"></a>語法

```
embedded_idl[("param")]
```

### <a name="parameters"></a>參數

*param*<br/>
可以是下列兩個值之一：

- **emitidl**： 從 typelib 匯入的類型資訊會出現在針對屬性化專案產生的 IDL 中。  這是預設值，如果未指定 `embedded_idl` 的參數就會生效。

- **no_emitidl**： 從 typelib 匯入的類型資訊將不會出現在針對屬性化專案產生的 IDL 中。

## <a name="example"></a>範例

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

## <a name="remarks"></a>備註

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)