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
ms.openlocfilehash: 42e8cc9a20c96e65ed3ddf73d562fe014bd9fa28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349995"
---
# <a name="partial--ccli-and-ccx"></a>partial  (C++/CLI 和 C++/CX)

**partial** 關鍵字可讓您在不同的檔案中個別撰寫相同 ref 類別的不同部分。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能僅適用於 Windows 執行階段。)

## <a name="windows-runtime"></a>Windows 執行階段

對於具有兩個部分定義的 ref 類,**部分**關鍵字應用於定義的第一次出現,這通常是透過自動生成的代碼完成的,以便人工編碼器不會經常使用該關鍵字。 如需類別的所有後續部分定義，請將 **partial** 修飾詞自 *class-key* 關鍵字和類別識別碼中省略。 當編譯器遇到先前定義的 ref 類別和類別識別碼，但沒有 **partial** 關鍵字時，它會在內部將 ref 類別定義的所有部分合併成一個定義。

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

*識別碼*<br/>
已定義型別的名稱。

### <a name="remarks"></a>備註

部分類別支援以下案例：您在一個檔案中修改一部分的類別定義，而自動產生程式碼的軟體 (例如 XAML 設計工具) 在另一個檔案中修改同一類別的程式碼。 您可以使用部分類別防止自動程式碼產生器覆寫您的程式碼。 在 Visual Studio 專案中，會對產生的檔案自動套用 **partial** 修飾詞。

內容:除兩個例外外,如果省略**了部分**關鍵字,則部分類定義可以包含完全類定義可能包含的任何內容。 不過，您無法指定類別存取範圍 (例如 `public partial class X { ... };`) 或 **declspec**。

*identifier* 的部分類別定義中所使用的存取規範，不會影響 *identifier* 的後續部分或完整類別定義中的預設存取範圍。 此外也允許靜態資料成員的內嵌定義。

聲明:類*識別符*的部分定義僅引入名稱*標識符*,但*識別符*不能以需要類定義的方式使用。 *identifier* 這個名稱無法用來取得 *identifier* 大小的資訊，也無法在編譯器遇到 *identifier* 的完整定義之前使用 *identifier* 的基底或成員。

編號和排序:*標記可*有零個或多個部分類定義。 *identifier* 的所有部分類別定義都必須在語彙上位於一個 *identifier* 完整定義前面 (如果有完整定義的話。否則，除非是在向前宣告的情況下，不然就無法使用該類別)，但是不需要在 *identifier* 的向前宣告之前。 所有的類別識別碼都必須相符。

完整定義:在類*標識符*的完整定義點,行為與*標識符*的定義聲明所有基類、成員等相同,其順序是部分類中遇到和定義它們。

範本:部分類不能是範本。

泛型:如果完整定義可以是泛型,則部分類可以是泛型。 但每個部分和完整類別都必須有完全相同的泛型參數，包括型式參數名稱。

如需如何使用 **partial** 關鍵字的詳細資訊，請參閱[部分類別 (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(這個語言功能不適用於 Common Language Runtime。)

## <a name="see-also"></a>另請參閱

[部分類別(C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
