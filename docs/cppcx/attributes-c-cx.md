---
title: 屬性 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371874"
---
# <a name="attributes-ccx"></a>屬性 (C++/CX)

屬性是一種特殊的 ref 類,可以在方括弧中預置到 Windows 運行時類型和方法,以指定中繼資料創建中的某些行為。 多個預定義屬性(例如[,Windows::基礎:元數據::WebHostHidden)](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)通常用於C++/CX 代碼。 此範例顯示如何將屬性套用至類別：

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>自訂屬性

您也可以定義自訂屬性。 自訂屬性必須符合以下 Windows 執行時規則:

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
[C++/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
