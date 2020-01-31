---
title: 列舉 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: be11d8d8f38a92fbe4be00eed53dd5226bab0b59
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821749"
---
# <a name="enums-ccx"></a>列舉 (C++/CX)

C++/CX 支援 `public enum class` 關鍵字，這類似于標準C++ `scoped  enum`。 當您使用以 `public enum class` 關鍵字所宣告的列舉程式時，您必須使用列舉識別項來限定每一個列舉值的範圍。

### <a name="remarks"></a>備註

不具有存取規範 (例如 `public enum class` ) 的 `public`視為標準 C++ [限定範圍列舉](../cpp/enumerations-cpp.md)。

`public enum class` 或 `public enum struct` 宣告可以有任何整數類資料類型的基礎類型，雖然 Windows 執行階段本身要求該類型必須為 int32，或 flags 用於旗標列舉。 下列語法描述 `public enum class` 或 `public enum struct`的部分。

本範例示範如何定義公用列舉類別：

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

下一個範例示範如何使用該類別：

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>範例

下面的範例示範如何宣告列舉，

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

下一個範例示範如何轉型為數值對應項及執行比較。 請注意，列舉程式 `One` 由 `Enum1` 列舉識別項界定使用範圍，列舉程式 `First` 由 `Enum2`界定範圍。

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>請參閱

[類型系統](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
