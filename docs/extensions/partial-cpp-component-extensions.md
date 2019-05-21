---
title: partial  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: eb9b3907008147cb21f04aec5f42e4896fa35b3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516473"
---
# <a name="partial--ccli-and-ccx"></a>partial  (C++/CLI 和 C++/CX)

**partial** 關鍵字可讓您在不同的檔案中個別撰寫相同 ref 類別的不同部分。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能僅適用於 Windows 執行階段。)

## <a name="windows-runtime"></a>Windows 執行階段

對於有兩個部分定義的 ref 類別，**partial** 關鍵字會套用至第一個定義，而且這通常是由自動產生的程式碼完成，因此編碼人員並不常使用這個關鍵字。 如需類別的所有後續部分定義，請將 **partial** 修飾詞自 *class-key* 關鍵字和類別識別碼中省略。 當編譯器遇到先前定義的 ref 類別和類別識別碼，但沒有 **partial** 關鍵字時，它會在內部將 ref 類別定義的所有部分合併成一個定義。

### <a name="syntax"></a>語法

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>參數

*class-key*<br/>
此關鍵字會宣告 Windows 執行階段支援的類別或結構。 任一 **ref class**、**value class**、**ref struct** 或 **value struct**。

*identifier*<br/>
已定義型別的名稱。

### <a name="remarks"></a>備註

部分類別支援以下案例：您在一個檔案中修改一部分的類別定義，而自動產生程式碼的軟體 (例如 XAML 設計工具) 在另一個檔案中修改同一類別的程式碼。 您可以使用部分類別防止自動程式碼產生器覆寫您的程式碼。 在 Visual Studio 專案中，會對產生的檔案自動套用 **partial** 修飾詞。

內容: 有兩個例外狀況，如果省略 **partial** 關鍵字，部分類別定義即可包含完整類別定義所能包含的任何項目。 不過，您無法指定類別存取範圍 (例如 `public partial class X { ... };`) 或 **declspec**。

*identifier* 的部分類別定義中所使用的存取規範，不會影響 *identifier* 的後續部分或完整類別定義中的預設存取範圍。 此外也允許靜態資料成員的內嵌定義。

宣告：*identifier* 類別的部分定義只會引入名稱 *identifier*，但是 *identifier* 無法以需要類別定義的方式使用。 *identifier* 這個名稱無法用來取得 *identifier* 大小的資訊，也無法在編譯器遇到 *identifier* 的完整定義之前使用 *identifier* 的基底或成員。

數目和順序：*identifier* 可以有零個或多個部分類別定義。 *identifier* 的所有部分類別定義都必須在語彙上位於一個 *identifier* 完整定義前面 (如果有完整定義的話。否則，除非是在向前宣告的情況下，不然就無法使用該類別)，但是不需要在 *identifier* 的向前宣告之前。 所有的類別識別碼都必須相符。

完整定義：在進行類別 *identifier* 的完整定義時，行為就如同 *identifier* 的定義已宣告所有基底類別、成員等 (宣告順序取決於在部分類別中遇到及定義這些項目的順序)。

範本：部分類別不可做為樣板。

泛型：如果完整定義可以是泛型，部分類別也可以是泛型。 但每個部分和完整類別都必須有完全相同的泛型參數，包括型式參數名稱。

如需如何使用 **partial** 關鍵字的詳細資訊，請參閱[部分類別 (C++/CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(這個語言功能不適用於 Common Language Runtime。)

## <a name="see-also"></a>另請參閱

[部分類別 (C++/CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)