---
title: 命名空間和類型可視性 (C++/CX)
ms.date: 12/30/2016
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
ms.openlocfilehash: cbfbd8c27065121eb176d9a62662eab7e1f4271b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230970"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>命名空間和類型可視性 (C++/CX)

命名空間是標準 C++ 建構，可將具有相關功能的類型組合在一起，並防止程式庫中發生名稱衝突。 Windows 執行階段類型系統要求必須在命名空間範圍的命名空間中宣告所有公用 Windows 執行階段類型（包括您自己程式碼中的）。 在全域範圍中宣告或以巢狀方式存在於其他類別中的公用型別會造成編譯時期錯誤。

.winmd 檔案必須具有根命名空間的相同名稱。 例如，名為 A.B.C.MyClass 的類別必須在名為 A.winmd、A.B.winmd 或 A.B.C.winmd 的中繼資料檔案中定義，才能執行個體化。 可執行檔的名稱不需符合 .winmd 檔案名稱。

## <a name="type-visibility"></a>型別可視性

在命名空間中，Windows 執行階段類型（不同于標準 c + + 類型）具有私用或公用存取範圍。 存取範圍預設為私用。 只有一個公用類型在中繼資料中是可見的，因此您可以從可能使用 C++ 以外之語言撰寫的應用程式和元件使用此類型。 一般而言，可見類型的規則比不可見類型的規則更嚴格，因為可見類型無法公開 .NET 語言或 JavaScript 不支援的 C++ 特定概念。

> [!NOTE]
> .NET 語言和 JavaScript 只有在執行階段才會使用中繼資料。 當 C++ 應用程式或元件與其他 C++ 應用程式或元件 (包括 Windows 元件) 通訊時，由於都是以 C++ 撰寫，因此不需要在執行階段使用中繼資料。

## <a name="member-accessibility-and-visibility"></a>成員存取範圍和可視性

在私用 ref 類別、介面或委派中，不會將任何成員發出至中繼資料，即使這些成員具有公用存取範圍亦然。 在公用 ref 類別中，您可以單獨控制中繼資料之成員的可視性，而不需要考量這些成員在原始程式碼中的存取範圍。 如同 Standard C++，請套用最低權限原則；除非絕對必要，否則請不要在中繼資料內顯示成員。

使用下列存取修飾詞控制中繼資料可視性和原始程式碼存取範圍。

||||
|-|-|-|
|修飾詞|意義|發出至中繼資料？|
|private|預設存取範圍。 等同於在 Standard C++ 中。|否|
|受保護|等同於在 Standard C++ 中，同時在應用程式 (或元件) 和中繼資料內。|是|
|公開|等同於在 Standard C++ 中。|是|
|`public protected` -或- `protected public`|在中繼資料內為受保護存取範圍，在應用程式或元件內是公用的。|是|
|`protected private` 或 `private protected`|在中繼資料內是不可見的，在應用程式或元件內為受保護存取範圍。||
|`internal` 或 `private public`|此成員在應用程式或元件內是公用的，但是在中繼資料內是不可見的。|否|

## <a name="windows-runtime-namespaces"></a>Windows 執行階段命名空間

Windows API 是由在 Windows：：命名空間中宣告的類型所組成 \* 。 這些命名空間保留給 Windows，不能在其中加入類型。 在 [ **物件瀏覽器**] 中，您可以檢視 windows.winmd 檔案中的命名空間。 如需這些命名空間的文件，請參閱 [Windows API](/uwp/api/)。

## <a name="ccx-namespaces"></a>C++/CX 命名空間

C + +/CX 會在 Windows 執行階段類型系統的投影中定義這些命名空間中的某些類型。

|||
|-|-|
|**Namespace**|**說明**|
|預設|包含內建的數字和 char16 類型。 這些類型位於每個命名空間的範圍內，而且 **`using`** 永遠不需要語句。|
|平台|主要包含對應至 Windows 執行階段類型（例如 `Array<T>` 、、和）的公用類型 `String` `Guid` `Boolean` 。 同時也包含特製化協助程式類型，例如 `Platform::Agile<T>` 和 `Platform::Box<T>`。|
|Platform::Collections|包含實作為 Windows 執行階段集合介面的實體集合類別， `IVector` `IMap` 等等。 這些類型在標頭檔 collection.h 中定義，而不是在 platform.winmd 中。|
|Platform::Details|包含編譯器使用的類型，而不開放使用。|

## <a name="see-also"></a>另請參閱

[類型系統 (C++/CX)](../cppcx/type-system-c-cx.md)
