---
title: 屬性 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 13a2639a877d1ba926d74511addcf72763967d85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462240"
---
# <a name="attributes-ccx"></a>屬性 (C++/CX)

屬性是一種特殊的 ref 類別，可附加至 Windows 執行階段型別和方法，以指定建立中繼資料時的特定行為的方括號中。 數個預先定義的屬性 — 例如， [1&gt;{2&gt;windows::foundation::metadata::webhosthidden&lt;2](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)— 常用在 C + + /CX 程式碼。 此範例顯示如何將屬性套用至類別：

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>自訂屬性

您也可以定義自訂屬性。 自訂屬性必須符合這些 Windows 執行階段規則：

- 自訂屬性只能包含公用欄位。

- 將屬性套用至類別之後，即可初始化自訂屬性欄位。

- 欄位可以是下列其中一種類型：

   - int32 (int)

   - uint32 (unsigned int)

   - bool

   - Platform::String^

   - Windows::Foundation::HResult

   - Platform::Type^

   - 公用列舉類別 (包括使用者定義的列舉)

下一個範例示範如何定義自訂屬性，然後在使用時予以初始化。

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>另請參閱

[類型系統 (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)