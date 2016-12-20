---
title: "code_seg (__declspec) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "code_seg_cpp"
  - "code_seg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "code_seg __declspec 關鍵字"
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# code_seg (__declspec)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `code_seg` 宣告屬性會為 .obj 檔中的可執行檔文字段落命名，函式或類別成員函式的目的碼將儲存在此 .obj 檔中。  
  
## 語法  
  
```  
__declspec(code_seg("segname")) declarator  
```  
  
## 備註  
 `__declspec(code_seg(...))` 屬性可用於將程式碼分為單獨的具名區段，而且這些區段可個別分頁或鎖定在記憶體中。  您可以使用這個屬性控制具現化的範本及編譯器產生之程式碼的位置。  
  
 .obj 檔中的「*區段*」\(Segment\) 是載入成為記憶體單位的具名資料區塊。  「*文字區段*」\(Text Segment\) 是包含可執行程式碼的區段。  「*區段*」\(Section\) 一詞常與「區段」\(segment\) 互換。  
  
 定義 `declarator` 時所產生的目的碼會在 `segname` \(窄字串常值\) 所指定的文字區段中。  在宣告中使用 `segname` 名稱之前，不需在[區段](../preprocessor/section.md) pragma 中指定該名稱。  根據預設，若未指定任何 `code_seg`，目的碼的位置會在區段具名 .text 中。  `code_seg` 屬性會覆寫任何現有的 [\#pragma code\_seg](../preprocessor/code-seg.md) 指示詞。  套用至成員函式的 `code_seg` 屬性會覆寫套用至封入類別的 `code_seg` 屬性。  
  
 如果實體具有 `code_seg` 屬性，相同實體的所有宣告和定義都必須有相同的 `code_seg` 屬性。  如果基底類別具有 `code_seg` 屬性，衍生類別必須具有相同的屬性。  
  
 當 `code_seg` 屬性套用至命名空間範圍函式或成員函式時，該函式的目的碼會在指定的文字區段中。  當這個屬性套用至類別時，該類別及巢狀類別的所有成員函式 \(包括編譯器產生的特殊成員函式\) 都會在指定的區段中。  本機定義的類別 \(例如在成員函式主體中定義的類別\) 不會繼承封閉範圍的 `code_seg` 屬性。  
  
 當 `code_seg` 屬性套用至樣板類別或樣板函式時，該樣板的所有隱含特製化都會在指定的區段中。  明確或部分特製化不會繼承主要樣板的 `code_seg` 屬性。  您可以在特製化指定相同或不同的 `code_seg` 屬性。  不可將 `code_seg` 屬性套用至明確樣板具現化。  
  
 根據預設，編譯器產生的程式碼 \(如特殊成員函式\) 會在 .text 區段中。  `#pragma code_seg` 指示詞不會覆寫這個預設值。  在類別、類別樣板或函式樣板使用 `code_seg` 屬性控制編譯器產生的程式碼的位置。  
  
 Lambda 會繼承其封閉範圍的 `code_seg` 屬性。  若要指定 Lambda 的區段，請在參數宣告子句之後、任何可變動或例外狀況規格、任何結尾傳回類型規格及 Lambda 本體之前套用 `code_seg` 屬性。  如需詳細資訊，請參閱[Lambda 運算式語法](../cpp/lambda-expression-syntax.md)。  這個範例會在名為 PagedMem 的區段中定義 Lambda：  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 當您將特定成員函式 \(尤其是虛擬成員函式\) 放在不同的區段時，請特別小心。  若基底類別方法位於非分頁區段，而您在位於分頁區段之衍生類別中定義虛擬函式，其他基底類別方法或使用者程式碼可能會假設叫用該虛擬方法不會觸發分頁錯誤。  
  
## 範例  
 這個範例示範 `code_seg` 屬性如何在使用隱含和明確樣板特製化時控制區段位置：  
  
```  
// code_seg.cpp  
// Compile: cl /EHsc /W4 code_seg.cpp  
  
// Base template places object code in Segment_1 segment  
template<class T>  
class __declspec(code_seg("Segment_1")) Example  
{  
public:  
   virtual void VirtualMemberFunction(T /*arg*/) {}  
};  
  
// bool specialization places code in default .text segment  
template<>  
class Example<bool>   
{  
public:  
   virtual void VirtualMemberFunction(bool /*arg*/) {}  
};  
  
// int specialization places code in Segment_2 segment  
template<>  
class __declspec(code_seg("Segment_2")) Example<int>   
{  
public:  
   virtual void VirtualMemberFunction(int /*arg*/) {}  
};  
  
// Compiler warns and ignores __declspec(code_seg("Segment_3"))  
// in this explicit specialization  
__declspec(code_seg("Segment_3")) Example<short>; // C4071  
  
int main()  
{  
   // implicit double specialization uses base template's  
   // __declspec(code_seg("Segment_1")) to place object code  
   Example<double> doubleExample{};  
   doubleExample.VirtualMemberFunction(3.14L);  
  
   // bool specialization places object code in default .text segment  
   Example<bool> boolExample{};  
   boolExample.VirtualMemberFunction(true);  
  
   // int specialization uses __declspec(code_seg("Segment_2"))  
   // to place object code  
   Example<int> intExample{};  
   intExample.VirtualMemberFunction(42);  
}  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)