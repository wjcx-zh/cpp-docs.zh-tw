---
title: "partial (C++ 元件擴充功能) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "partial_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partial"
  - "C++/CX，partial"
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# partial (C++ 元件擴充功能)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`partial` 關鍵字允許在不同的檔案中獨立撰寫相同 ref 類別的不同部分。  
  
## 所有執行階段  
 \(這個語言功能只適用於 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]\)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 對於有兩個部分定義的 ref 類別，`partial` 關鍵字會套用至定義的第一個項目，這通常是由自動產生的程式碼完成，因此程式碼編寫人員一般都不會經常使用這個關鍵字。  對於類別所有的後續部分定義，請省略「*類別機碼*」\(Class\-key\) 關鍵字及類別識別項中的 `partial` 修飾詞。  當編譯器遇到先前定義的 ref 類別與類別識別項，但沒有 `partial` 關鍵字時，就會在內部將 ref 類別定義的所有部分合併一個定義。  
  
### 語法  
  
```cpp  
  
partial class-key identifier {  
   /* The first part of the partial class definition. This is typically auto-generated*/  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same identifier is specified, but the "partial" keyword is omitted. */  
}  
  
```  
  
### 參數  
 *class\-key*  
 宣告 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 所支援之類別或結構的關鍵字。  `ref class`、`value class`、`ref struct` 或 `value struct`。  
  
 *identifier*  
 定義的型別的名稱。  
  
### 備註  
 部分類別會下列支援情節：您在一個檔案中修改類別定義的某個部分，而自動產生程式碼軟體 \(例如 XAML 設計工具\) 也在另一個檔案中修改相同類別中的程式碼。  您可以使用部分類別，防止自動程式碼產生器覆寫您的程式碼。  在 Visual Studio 專案中，會對產生的檔案自動套用 `partial` 修飾詞。  
  
 內容：有兩個例外情況。如果省略 `partial` 關鍵字，則部分類別定義可以包含完整類別定義所能包含的任何項目。  不過，您無法指定類別存取範圍 \(例如 `public partial class X {…};`\) 或 `declspec`。  
  
 用於*identifier* 之部分類別定義的存取規範，不會影響 *identifier* 後續之部分或完整類別定義中的預設存取範圍。  允許靜態資料成員的內嵌定義。  
  
 宣告：*identifier* 類別的部分定義只引入名稱 *identifier*，但是 *identifier* 無法在需要類別定義的方式下使用。  名稱 *identifier* 無法用來得知 *identifier* 的大小，也無法藉以在編譯器遇到 *identifier* 的完整定義之前使用 *identifier* 的基底或成員。  
  
 數字和順序：*identifier*可以有零個或多個部分類別定義。  *identifier* 的所有部分類別定義都必須在語彙上居於 *identifier* 的某個完整定義之先 \(如果有完整定義的話。否則，除非是在向前宣告的情況下，不然就無法使用該類別\)，但是不需要在 *identifier* 的向前宣告之前。  所有的類別機碼都必須相符。  
  
 在進行類別 *identifier* 的完整定義時，運作方式會如同 *identifier* 的定義已宣告所有的基底類別、成員等項目 \(宣告順序取決於在部分類別中發現及定義這些項目的順序\)。  
  
 範本：部分類別不可以是範本。  
  
 泛型：如果完整定義可以是泛型，部分類別就可以是泛型。  但是每個部分或完整類別都必須具有完全相同的泛型參數，包括型式參數名稱。  
  
 如需使用 `partial` 關鍵字的詳細資訊，請參閱 [部分類別 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 \(這個語言功能不適用於 Common Language Runtime\)。  
  
## 請參閱  
 [部分類別 \(C\+\+\/CX\)](http://go.microsoft.com/fwlink/p/?LinkId=249023)