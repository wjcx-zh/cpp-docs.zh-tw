---
title: partial （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 340323d2b540c74e600b76129edd360b73d0db23
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372132"
---
# <a name="partial--c-component-extensions"></a>partial (C++ 元件擴充功能)

**部分**關鍵字可讓不同的組件相同的 ref 類別，可撰寫彼此獨立，而且在不同的檔案。

## <a name="all-runtimes"></a>所有執行階段

（這個語言功能只套用至 Windows 執行階段。）

## <a name="windows-runtime"></a>Windows 執行階段

有兩個部分定義，ref 類別**部分**關鍵字是否套用至第一個定義，以及這通常是由自動產生的程式碼，好讓人類 coder 不經常使用關鍵字。 如需所有後續部分定義的類別，請省略**部分**修飾詞*class 索引鍵*關鍵字和類別識別項。 當編譯器遇到先前定義的 ref 類別和類別識別項，但沒有**部分**關鍵字，在內部結合了所有 ref 類別定義貼入一個定義的組件。

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

*類別索引鍵*<br/>
關鍵字會宣告類別或結構所支援的 Windows 執行階段。 任一**ref 類別**，**的實值類別**， **ref struct**，或**實值結構**。

*identifier*<br/>
定義型別的名稱。

### <a name="remarks"></a>備註

部分類別支援，您可以修改一個檔案，並自動產生程式碼軟體中的類別定義的某一部分的案例 — 比方說，XAML 設計工具 — 修改另一個檔案中的相同類別中的程式碼。 藉由使用部分類別，您可以避免自動程式碼產生器覆寫您的程式碼。 在 Visual Studio 專案中，**部分**修飾詞會自動套用至所產生的檔案。

內容： 有兩個例外狀況，部分類別定義可以包含任何項目可以包含完整類別定義，如果**部分**關鍵字已省略。 不過，您不能指定類別存取範圍 (例如`public partial class X { ... };`)，或有**declspec**。

存取規範的部分類別定義中使用*識別碼*不會影響在後續的部分或完整類別定義中的預設存取範圍*識別項*。 允許靜態資料成員的內嵌定義。

宣告： 部分類別定義*識別碼*只會引入名稱*識別項*，但*識別碼*不能用在需要的類別的方法定義。 名稱*識別碼*不能用來了解的大小*識別項*，或若要使用的基底或成員*識別碼*直到編譯器遇到的完整定義之後*識別碼*。

數目與順序： 可以有零個或多個部分類別定義*識別碼*。 每個部分類別定義*識別碼*語彙必須在前面的一個完整定義*識別項*(如果有完整的定義; 否則類別不能用除了如同向前宣告），但不是需要在前面的向前宣告*識別碼*。 必須符合所有的類別索引鍵。

完整定義： 類別的完整定義時會*識別碼*，行為是相同一樣的定義*識別項*已宣告所有基底類別、 成員等中的順序他們遇到及定義在部分類別。

範本： 部分類別不可為樣板。

泛型： 部分類別可以是泛型如果完整的定義可能是泛型。 但每個部分和完整的類別必須完全相同泛型參數，包括型式參數名稱。

如需有關如何使用**部分**關鍵字，請參閱[部分類別 (C + + /CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

（這個語言功能不適用於通用語言執行平台。）

## <a name="see-also"></a>另請參閱

[部分類別 (C + + /CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)