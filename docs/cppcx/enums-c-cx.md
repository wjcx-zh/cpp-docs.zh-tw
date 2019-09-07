---
title: 列舉 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 3bdcff03872dcfe83f0be5752cec4f567fbc6b72
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740216"
---
# <a name="enums-ccx"></a>列舉 (C++/CX)

C++/Cx 支援類似于`public enum class`為標準C++ `scoped  enum`的關鍵字。 當您使用以 `public enum class` 關鍵字所宣告的列舉程式時，您必須使用列舉識別項來限定每一個列舉值的範圍。

### <a name="remarks"></a>備註

不具有存取規範 (例如 `public enum class` ) 的 `public`視為標準 C++ [限定範圍列舉](../cpp/enumerations-cpp.md)。

雖然 Windows 執行階段`public enum struct`本身會要求類型必須是 int32，或旗標列舉的 uint32，或宣告可以具有任何整數類型的基礎類型。`public enum class` 下列語法描述 `public enum class` 或 `public enum struct`的部分。

本範例示範如何定義公用列舉類別：

[!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]

下一個範例示範如何使用該類別：

[!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]

### <a name="examples"></a>範例

下面的範例示範如何宣告列舉，

[!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]

下一個範例示範如何轉型為數值對應項及執行比較。 請注意，列舉程式 `One` 由 `Enum1` 列舉識別項界定使用範圍，列舉程式 `First` 由 `Enum2`界定範圍。

[!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]

## <a name="see-also"></a>另請參閱

[類型系統](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
