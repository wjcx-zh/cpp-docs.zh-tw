---
title: code_seg (__declspec) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- code_seg_cpp
dev_langs:
- C++
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dcf387283aa0d4cdb282760c4ee170a0205172d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068812"
---
# <a name="codeseg-declspec"></a>code_seg (__declspec)

**Microsoft 專屬**

**Code_seg**宣告屬性名稱的可執行檔的文字區段，將儲存的函式或類別成員函式的物件程式碼的.obj 檔案中。

## <a name="syntax"></a>語法

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>備註

`__declspec(code_seg(...))` 屬性可用於將程式碼分為單獨的具名區段，而且這些區段可個別分頁或鎖定在記憶體中。 您可以使用這個屬性控制具現化的範本及編譯器產生之程式碼的位置。

A*區段*是載入成為記憶體單位的.obj 檔案中的資料的具名的區塊。 A*文字區段*是包含可執行程式碼區段。 詞彙*一節*區段經常交換使用。

定義 `declarator` 時所產生的目的碼會在 `segname` (窄字串常值) 所指定的文字區段中。 名稱`segname`不需要指定[一節](../preprocessor/section.md)pragma 才可以在宣告中使用。 根據預設，若未指定任何 `code_seg`，目的碼的位置會在區段具名 .text 中。 A **code_seg**屬性會覆寫任何現有[#pragma code_seg](../preprocessor/code-seg.md)指示詞。 A **code_seg**屬性套用至成員函式會覆寫任何**code_seg**套用至封入類別的屬性。

如果實體有**code_seg**屬性中，所有宣告和定義相同的實體都必須都有相同**code_seg**屬性。 如果基底類別具有**code_seg**屬性，衍生類別必須具有相同的屬性。

當**code_seg**屬性套用至命名空間範圍函式或成員函式，該函式的物件程式碼會放在指定的文字區段。 當這個屬性套用至類別時，該類別及巢狀類別的所有成員函式 (包括編譯器產生的特殊成員函式) 都會在指定的區段中。 在本機定義的類別 — 比方說，成員函式主體中定義的類別，並不會繼承**code_seg**封閉範圍的屬性。

當**code_seg**屬性套用至樣板類別或樣板函式，範本的所有隱含特製化都會在指定的區段。 明確或部分特製化不會繼承**code_seg**從主要範本的屬性。 您可以指定相同或不同**code_seg**在特製化的屬性。 A **code_seg**屬性無法套用至明確樣板具現化。

根據預設，編譯器產生的程式碼 (如特殊成員函式) 會在 .text 區段中。 `#pragma code_seg` 指示詞不會覆寫這個預設值。 使用**code_seg**類別、 類別樣板或函式樣板，編譯器產生的程式碼要在其中放置控制項的屬性。

Lambda 會繼承**code_seg**其封閉範圍的屬性。 若要指定 lambda 的區段，套用**code_seg**屬性的參數宣告子句之後，以及之前任何可變動或例外狀況規格，任何尾端傳回型別規格，而且 lambda 主體。 如需詳細資訊，請參閱 < [Lambda 運算式語法](../cpp/lambda-expression-syntax.md)。 這個範例會在名為 PagedMem 的區段中定義 Lambda：

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

當您將特定成員函式 (尤其是虛擬成員函式) 放在不同的區段時，請特別小心。 若基底類別方法位於非分頁區段，而您在位於分頁區段之衍生類別中定義虛擬函式，其他基底類別方法或使用者程式碼可能會假設叫用該虛擬方法不會觸發分頁錯誤。

## <a name="example"></a>範例

此範例示範如何**code_seg**屬性控制區段位置時隱含和明確樣板特製化會使用：

```cpp
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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)