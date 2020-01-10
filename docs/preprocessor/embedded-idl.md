---
title: embedded_idl 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216322"
---
# <a name="embedded_idl-import-attribute"></a>embedded_idl 匯入屬性

**C++特殊**

指定是否要`.tlh`將類型程式庫寫入檔案, 並保留屬性產生的程式碼。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***embedded_idl**[ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>參數

**emitidl**\
從*型別程式庫*匯入的類型資訊存在於針對屬性化專案產生的 IDL 中。 這個行為是預設值, 如果您未指定的參數`embedded_idl`, 則會生效。

**"no_emitidl"** \
從*型別程式庫*匯入的類型資訊不會出現在針對屬性化專案產生的 IDL 中。

## <a name="example"></a>範例

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
