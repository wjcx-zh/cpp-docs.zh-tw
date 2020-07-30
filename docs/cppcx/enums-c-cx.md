---
title: 列舉 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
ms.openlocfilehash: 54e413e65b3130b9b83e6d1ed56b5ee87b84e0a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225757"
---
# <a name="enums-ccx"></a>列舉 (C++/CX)

C + +/CX 支援 `public enum class` 關鍵字，類似于標準 c + + `scoped  enum` 。 當您使用以 `public enum class` 關鍵字所宣告的列舉程式時，您必須使用列舉識別項來限定每一個列舉值的範圍。

### <a name="remarks"></a>備註

`public enum class`不具有存取規範（例如 **`public`** ）的會被視為標準 c + +[範圍列舉](../cpp/enumerations-cpp.md)。

`public enum class` `public enum struct` 雖然 Windows 執行階段本身會要求類型必須是 int32，或旗標列舉的 uint32，或宣告可以具有任何整數類型的基礎類型。 下列語法描述 `public enum class` 或 `public enum struct`的部分。

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

[型別系統](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
