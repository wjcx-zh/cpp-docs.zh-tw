---
title: Ref 類別與結構 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: d128734f8c78c9198f0731b415c1be35b0c58e65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214954"
---
# <a name="ref-classes-and-structs-ccx"></a>Ref 類別與結構 (C++/CX)

C + +/CX 支援使用者定義的*ref 類別*和*ref 結構*，以及使用者定義的實*值類別*和*值結構*。 這些資料結構是 c + +/CX 支援 Windows 執行階段型別系統的主要容器。 其內容會根據某些特定規則發出給中繼資料，這可讓它們在 Windows 執行階段元件和以 c + + 或其他語言撰寫的通用 Windows 平臺應用程式之間傳遞。

ref 類別或 ref 結構具有這些必要功能：

- 您必須在命名空間中 (在命名空間範圍) 宣告此類別，且此類別在該命名空間中可以具有公用或私用存取範圍。 只有公用型別會發出至中繼資料。 不允許巢狀公用類別定義，包括巢狀公用 [列舉](../cppcx/enums-c-cx.md) 類別。 如需詳細資訊，請參閱[命名空間和類型可見度](../cppcx/namespaces-and-type-visibility-c-cx.md)。

- 它可以包含 as 成員 c + +/CX，包括 ref 類別、實值類別、ref 結構、值結構或可為 null 的值結構。 它也可以包含純量類型 `float64` ，例如、 **`bool`** 等等。 它也可以包含標準 C++ 類型 (例如 `std::vector` ) 或自訂類別，只要這些不是公用項目即可。 C + +/cx 結構可能具有 **`public`** 、 **`protected`** 、 **`internal`** 、 **`private`** 或 **`protected private`** 存取範圍。 所有 **`public`** 或 **`protected`** 成員都會發出至中繼資料。 Standard c + + 類型必須具有 **`private`** 、 **`internal`** 或 **`protected private`** 存取範圍，以避免發出至中繼資料。

- 可以實作一個或多個「 *介面類別* 」(Interface Class) 或「 *介面結構*」(Interface Struct)。

- 可以繼承自一個基底類別，而基底類別本身會有其他限制。 公用 ref 類別階層中的繼承比私用 ref 類別中的繼承有更多限制。

- 不可以宣告為泛型。 如果具有私用存取範圍，可以是範本。

- 其存留期會由自動參考計數來管理。

## <a name="declaration"></a>宣告

下列程式碼片段會宣告 `Person` ref 類別。 請注意，standard c + + `std::map` 類型用於私用成員中，而 Windows 執行階段 `IMapView` 介面則用於公用介面中。 同時也請注意，參考類型的宣告附加了 "^"。

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>實作

此程式碼範例示範 `Person` ref 類別的實作：

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>使用方式

下一個程式碼範例則說明用戶端程式碼如何使用 `Person` ref 類別。

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

您也可以使用堆疊語意宣告區域 ref 類別變數。 即使記憶體仍是以動態方式配置的，這類物件的行為還是會類似於堆疊式變數。 一個重要的差異在於，您無法將追蹤參考 (%) 指派給使用堆疊語意宣告的變數，這可以確保參考計數在函式結束時將會減為零。 下列範例示範基本 ref 類別 `Uri`，以及將其與堆疊語意搭配使用的函式：

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>記憶體管理

您可以使用關鍵字，在動態記憶體中配置 ref 類別 **`ref new`** 。

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

物件控制碼運算子 **`^`** 稱為*hat* ，基本上是 c + + 智慧型指標。 當最後一個 hat 超出範圍或明確設定為時，會自動終結它所指向的記憶體 **`nullptr`** 。

根據定義，ref 類別具有參考語意。 當您指派 ref 類別變數時，所指派的會是複製的控制代碼，而不是物件本身。 在下一個範例中，進行指派後， `myClass` 和 `myClass2` 會指向相同的記憶體位置。

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

具現化 C++/CX ref 類別時，會在呼叫其建構函式之前，將其記憶體初始設定為零；因此，不需要對個別成員進行歸零初始設定作業 (包括屬性)。 如果 C++/CX 類別衍生自 Windows Runtime C++ Library (WRL) 類別，只會對 C++/CX 衍生類別部分進行歸零初始設定。

### <a name="members"></a>成員

Ref 類別可以包含 **`public`** 、和函式 **`protected`** **`private`** 成員; 只有 **`public`** 和 **`protected`** 成員會發出至中繼資料。 允許嵌套的類別和 ref 類別，但不可以是 **`public`** 。 不允許公用欄位；公用資料成員必須宣告為屬性。 私用或受保護的內部資料成員可以是欄位。 根據預設，在 ref 類別中，所有成員的存取範圍是 **`private`** 。

Ref 結構與 ref 類別相同，不同之處在于預設的成員具有 **`public`** 存取範圍。

**`public`** Ref 類別或 ref 結構會在中繼資料中發出，但若要從其他通用 Windows 平臺應用程式和 Windows 執行階段元件使用，它必須至少有一個公用或受保護的函式。 具有公用函數的公用 ref 類別也必須宣告為 **`sealed`** ，以防止透過應用程式二進位介面（ABI）進行進一步的衍生。

公用成員可能不會宣告為， **`const`** 因為 Windows 執行階段類型系統不支援 const。 您可以使用靜態屬性來宣告具有常數值的公用資料成員。

當您定義公用 ref 類別或結構時，編譯器會將必要的屬性套用至類別，並將該資訊存放在應用程式的 .winmd 檔案中。 不過，當您定義公用非密封 ref 類別時，請手動套用 `Windows::Foundation::Metadata::WebHostHidden` 屬性，以確保在以 JavaScript 撰寫的通用 Windows 平臺應用程式看不到該類別。

Ref 類別可以 **`const`** 在任何 **`private`** 、 **`internal`** 或成員中具有標準 c + + 類型，包括類型 **`protected private`** 。

不允許具有型別參數的公用 ref 類別。 不允許使用者定義的泛型 ref 類別。 私用、內部或受保護的私用 ref 類別可以是範本。

## <a name="destructors"></a>解構函式

在 c + +/CX 中，不論物件的參考計數為何，在公用析構函式上呼叫都會叫用 **`delete`** 此函式。 這個行為可讓您定義解構函式，該解構函式會以非常確定的方式執行非 RAII 資源的自訂清除。 不過，即使在這個情況下，物件本身還是不會從記憶體中刪除。 只有當參考計數到達零時，才會釋放此物件的記憶體。

如果類別的解構函式非公用，則只有當參考計數到達零時才會叫用它。 如果您 `delete` 在具有私用函式的物件上呼叫，編譯器會引發警告 C4493，這表示「刪除運算式沒有作用，因為的析構函式沒有「公用」存取範圍」 \<type name> 。

Ref 類別解構函式只能宣告如下：

- 公用和虛擬 (適用於密封或非密封類型)

- 受保護的私用和非虛擬 (適用於非密封類型)

- 私用和非虛擬 (僅適用於密封類型)

不允許存取範圍、虛擬及密封的其他任何組合。  如果您未明確宣告解構函式，則編譯器會在類型的基底類別或任何成員具有公用解構函式時，產生公用虛擬解構函式。 否則，編譯器會為非密封類型產生受保護的私用非虛擬解構函式，或為密封類型產生私用非虛擬解構函式。

如果您嘗試存取的類別成員已執行其解構函式，則表示此行為是未定義的；這很有可能會導致程式當機。 針對沒有公用解構函式的類型呼叫 `delete t` 沒有作用。 `delete this`針對在其類型階層內具有已知或析構函式的類型或基類呼叫 **`private`** **`protected private`** 也沒有任何作用。

當您宣告公用解構函式時，編譯器會產生程式碼，讓 ref 類別實作 `Platform::IDisposable` ，且解構函式實作 `Dispose` 方法。 `Platform::IDisposable`是的 c + +/CX 投射 `Windows::Foundation::IClosable` 。 絕對不要明確實作這些介面。

## <a name="inheritance"></a>繼承

Platform::Object 是所有 ref 類別的通用基底類別。 所有 ref 類別都會隱含轉換為 Platform::Object，而且也都能覆寫 [Object::ToString](../cppcx/platform-object-class.md#tostring)。 不過，Windows 執行階段繼承模型不適合做為一般繼承模型;在 c + +/CX 中，這表示使用者定義的公用 ref 類別不能做為基類。

如果您要建立 XAML 使用者控制項，而且物件參與相依性屬性系統，則您可以使用 `Windows::UI::Xaml::DependencyObject` 做為基底類別。

定義繼承自 `MyBase` 的未密封類別 `DependencyObject`之後，元件或應用程式中的其他公用或私用 ref 類別則可以繼承自 `MyBase`。 您應該只有在為了支援虛擬方法、多型識別及封裝的覆寫時，才執行公用 ref 類別中的繼承。

您不需要從現有的未密封類別衍生私用基底 ref 類別。 如果您需要物件階層建立您自己的程式結構模型，或允許重複使用程式碼，則使用私用或內部 ref 類別，或最好使用 Standard C++ 類別。 您可以透過公用密封 ref 類別包裝函式，公開私用物件階層的功能。

在 c + +/CX 中具有公用或受保護之函式的 ref 類別，必須宣告為 sealed。 這項限制表示，以 c # 或 Visual Basic 等其他語言撰寫的類別，無法繼承自您在以 c + +/CX。撰寫的 Windows 執行階段元件中宣告的類型。

以下是 c + +/CX 繼承的基本規則：

- ref 類別最多可直接繼承自一個基底 ref 類別，但可以實作任意數目的介面。

- 如果類別具有公用建構函式，也必須宣告為密封類別，以避免進一歩衍生。

- 您可以建立具有內部或受保護的私用建構函式之公用未密封基底類別，但是前提是此基底類別直接或間接衍生自現有的未密封基底類別，例如 `Windows::UI::Xaml::DependencyObject`。 不支援跨 .winmd 檔案繼承使用者定義的 ref 類別；但是，ref 類別可以繼承自其他 .winmd 檔案中定義的介面。 您只能在相同的 Windows 執行階段元件或通用 Windows 平臺應用程式中，從使用者定義的基底 ref 類別建立衍生類別。

- 針對 ref 類別，只支援公用繼承。

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

下列範例示範如何公開衍生自繼承階層中其他 ref 類別的公用 ref 類別。

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>另請參閱

[型別系統](../cppcx/type-system-c-cx.md)<br/>
[實值類別與結構](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
