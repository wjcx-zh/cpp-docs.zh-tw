---
title: make_public pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d12fab685e0088993cb43073c3603bda12edd2f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218827"
---
# <a name="make_public-pragma"></a>make_public pragma

表示原生類型應該具有公用組件存取範圍。

## <a name="syntax"></a>語法

> **#pragma make_public (** *類型* **)**

### <a name="parameters"></a>參數

*type*\
您想要具有公用元件存取範圍之類型的名稱。

## <a name="remarks"></a>備註

當您想要參考的原生類型來自您無法變更的標頭檔時, **make_public**會很有用。 如果您想要在具有公用元件可見度的類型中, 使用公用函式簽章中的原生類型, 原生類型也必須具有公用元件存取範圍, 否則編譯器會發出警告。

**make_public**必須指定于全域範圍。 它只會從其宣告到原始程式碼檔結尾的位置生效。

原生類型可以隱含或明確地私用。 如需詳細資訊, 請參閱[類型可見度](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)。

## <a name="examples"></a>範例

下列範例是標頭檔的內容, 其中包含兩個原生結構的定義。

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

下列程式碼範例會使用標頭檔。 它會顯示, 除非您使用**make_public**將原生結構明確標示為公用, 否則當您嘗試在公用 managed 類型中的公用函式簽章中使用原生結構時, 編譯器會產生警告。

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
