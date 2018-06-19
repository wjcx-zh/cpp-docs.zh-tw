---
title: partial （c + + 元件擴充功能） |Microsoft 文件
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
ms.openlocfilehash: 71c0fc9739e7ef8e1e68c5678ce56fcec4a250c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880175"
---
# <a name="partial--c-component-extensions"></a>partial (C++ 元件擴充功能)
`partial`關鍵字可讓相同的 ref 類別，來撰寫彼此獨立，而且在不同檔案中的不同部分。  
  
## <a name="all-runtimes"></a>所有執行階段  
 （這個語言功能只適用於 Windows 執行階段。）  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 有兩個部分定義，ref 類別`partial`關鍵字會套用至第一個出現的定義，而且這通常是自動產生的程式碼，以便人力編碼器不會經常使用關鍵字。 如需所有後續部分定義的類別，省略`partial`修飾詞從*類別索引鍵*關鍵字和類別識別項。 當編譯器遇到先前定義的 ref 類別和類別識別項，但不是`partial`關鍵字，在內部會結合到一個定義的 ref 類別定義組件。  
  
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
 *類別索引鍵*  
 關鍵字會宣告類別或結構支援的 Windows 執行階段。 任一`ref class`， `value class`， `ref struct`，或`value struct`。  
  
 *identifier*  
 定義類型的名稱。  
  
### <a name="remarks"></a>備註  
 部分類別支援讓您修改的一個檔案，並自動產生的程式碼軟體中的類別定義一個部分的案例 — 例如 XAML 設計工具 — 修改另一個檔案中的相同類別中的程式碼。 藉由使用部分類別，您可以防止自動程式碼產生器覆寫您的程式碼。 在 Visual Studio 專案中，會對產生的檔案自動套用 `partial` 修飾詞。  
  
 內容： 有兩個例外狀況，部分類別定義即可包含完整類別定義無法包含任何項目`partial`關鍵字已省略。 不過，您無法指定類別存取範圍 (例如 `public partial class X { ... };`) 或 `declspec`。  
  
 存取規範中的部分類別定義使用*識別碼*不會影響後續的部分或完整類別定義中的預設存取範圍*識別碼*。 允許靜態資料成員的內嵌定義。  
  
 宣告： 部分類別定義*識別碼*只是導入的名稱*識別碼*，但*識別碼*無法用於需要類別方法定義。 名稱*識別碼*不能用來知道的大小*識別碼*，或若要使用的基底或成員*識別碼*直到編譯器遇到的完整定義之後*識別碼*。  
  
 數目與順序： 可以有零個或多個部分類別定義*識別碼*。 每個部分類別定義*識別碼*語彙上皆必須在前面的一個完整定義*識別碼*(如果有完整的定義; 否則類別不能用除了如同向前宣告），但不是需要在之前的向前宣告*識別碼*。 所有的類別識別碼必須相符。  
  
 完整定義： 類別的完整定義時會*識別碼*，則行為是相同如同的定義*識別碼*宣告所有基底類別、 成員等等中的順序遇到和它們在部分類別中定義。  
  
 範本： 部分類別不可為樣板。  
  
 泛型： 部分類別可以是泛型如果完整定義可能是泛型。 但是，每個部分或完整的類別必須要有完全相同泛型參數包括型式參數名稱。  
  
 如需有關如何使用`partial`關鍵字，請參閱[部分類別 (C + + /CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 （這個語言功能不適用於通用語言執行平台。）  
  
## <a name="see-also"></a>另請參閱  
 [部分類別 (C + + /CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)