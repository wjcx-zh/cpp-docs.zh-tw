---
title: 部分類別 (C++/CX)
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 1f5583354481248e8df201be200fe99da61791dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185459"
---
# <a name="partial-classes-ccx"></a>部分類別 (C++/CX)

部分類別是支援下列案例的建構：您要修改一部分的類別定義，而自動產生程式碼軟體 (例如 XAML 設計工具) 也在相同的類別中修改程式碼。 使用部分類別可防止設計工具覆寫您的程式碼。 在 Visual Studio 專案中，會對產生的檔案自動套用 `partial` 修飾詞。

## <a name="syntax"></a>語法

若要定義部分類別，請在原本是一般類別定義之項目的類別識別碼之前使用 `partial` 關鍵字。 `partial ref class` 之類的關鍵字是包含空白字元的內容關鍵字。 支援部分定義的建構如下。

- **`class`** 或**`struct`**

- **`ref class`** 或**`ref struct`**

- **`value class`** 或**`value struct`**

- **`enum`** 或**`enum class`**

- `ref interface`、 **`interface class`** 、 **`interface struct`** 或 **' __interface**

- **`union`**

這個範例會示範部分 **`ref class`** ：

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>目錄

如果省略 `partial` 關鍵字，部分類別定義即可包含完整類別定義所能包含的任何項目。 除了一項例外狀況，這包括任何有效的建構，例如基底類別、資料成員、成員函式、列舉、friend 宣告和屬性。 此外也允許靜態資料成員的內嵌定義。

這項例外狀況是類別存取範圍。 例如，陳述式 `public partial class MyInvalidClass {/* ... */};` 是錯誤。 MyInvalidClass 的部分類別定義中所使用的任何存取規範，對於 MyInvalidClass 後續的部分或完整類別定義中的預設存取範圍都不會有影響。

下列程式碼片段示範存取範圍。 在第一個部分類別中， `Method1` 是公用的，因為其存取範圍是公用的。 在第二部分類別中， `Method2` 是私用的，因為預設的類別存取範圍是私用的。

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>宣告

*MyClass* 之類的部分類別定義，只是 MyClass 的宣告。 也就是說，它只是導入 *MyClass*這個名稱而已。 *MyClass* 無法用於需要類別定義的用途中，例如了解 *MyClass* 的大小，或使用 *MyClass*的基底或成員。 只有在編譯器找到*MyClass* 的非部分定義時，才會認定 *MyClass*已完成定義。

下列範例示範部分類別的宣告行為。 在宣告 #1 後面，可將 *MyClass* 視為已撰寫成向前宣告 `ref class MyClass;`來加以使用。 宣告 #2 等同於宣告 #1。宣告 #3 有效，因為它是類別的向前宣告。 然而，宣告 #4 則無效，因為

*MyClass* 並未經過完整定義。

宣告 #5 未使用 `partial` 關鍵字，且此宣告已完整定義 *MyClass*。 最後，宣告 #6 是有效的。

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>數目與順序

類別的每個完整定義都可以有零個或多個部分類別定義。

類別的每個部分類別定義在語彙上皆必須位於該類別的一個完整定義之前，但不一定要位於該類別的向前宣告之前。 如果類別沒有完整定義，部分類別宣告就只能是向前宣告。

所有的類別索引鍵（例如 **`class`** 和） **`struct`** 都必須相符。 例如，下列程式碼是錯誤的： `partial class X {}; struct X {};`這個名稱而已。

下列範例示範數目與順序。 最後一個部分宣告會失敗，因為類別已定義。

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>完整定義

在進行類別 X 的完整定義時，運作方式會如同 X 的定義已宣告所有的基底類別、成員等項目 (宣告順序取決於在部分類別中發現及定義這些項目的順序)。 也就是說，部分類別的內容會如同已在進行類別的完整定義時撰寫，而在進行類別的完整定義時會套用名稱查閱與其他語言規則，如同部分類別的內容已撰寫。

下列兩個程式碼範例具有相同的意義和效用。 第一個範例會使用部分類別，第二個範例則否。

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>範本

部分類別不可做為樣板。

## <a name="restrictions"></a>限制

部分類別不可延伸到其他轉譯單位。

`partial`關鍵字僅支援與 **`ref class`** 關鍵字或關鍵字一起使用 **`value class`** 。

### <a name="examples"></a>範例

下列範例會定義跨兩個程式碼檔案的 `Address` 類別。 設計工具可修改 `Address.details.h` ，而您可以修改 `Address.h`。 只有第一個檔案中的類別定義會使用 `partial` 關鍵字。

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>另請參閱

[型別系統](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
