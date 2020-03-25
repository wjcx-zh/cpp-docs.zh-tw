---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: 22703e92b1a127378c965ce12bcc4e5475b3e452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180832"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Microsoft 專屬**

**Code_seg**宣告屬性會為 .obj 檔案中的可執行文字區段命名，其中會儲存函式或類別成員函式的物件程式碼。

## <a name="syntax"></a>語法

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>備註

`__declspec(code_seg(...))` 屬性可用於將程式碼分為單獨的具名區段，而且這些區段可個別分頁或鎖定在記憶體中。 您可以使用這個屬性控制具現化的範本及編譯器產生之程式碼的位置。

「*區段*」（segment）是 .obj 檔案中的資料命名區塊，會當做一個單位載入至記憶體中。 「*文字區段」（text segment* ）是包含可執行程式碼的區段。 「詞彙」*一*詞通常會與「區段」交換使用。

定義 `declarator` 時所產生的目的碼會在 `segname` (窄字串常值) 所指定的文字區段中。 不需要在[區段](../preprocessor/section.md)pragma 中指定名稱 `segname`，就可以在宣告中使用它。 根據預設，若未指定任何 `code_seg`，目的碼的位置會在區段具名 .text 中。 **Code_seg**屬性會覆寫任何現有的[#pragma code_seg](../preprocessor/code-seg.md)指示詞。 套用至成員函式的**code_seg**屬性會覆寫套用至封入類別的任何**code_seg**屬性。

如果實體具有**code_seg**屬性，則相同實體的所有宣告和定義都必須具有相同的**code_seg**屬性。 如果基類具有**code_seg**屬性，衍生的類別必須具有相同的屬性。

當**code_seg**屬性套用至命名空間範圍函數或成員函式時，該函式的物件程式碼會放在指定的文字區段中。 當這個屬性套用至類別時，該類別及巢狀類別的所有成員函式 (包括編譯器產生的特殊成員函式) 都會在指定的區段中。 本機定義的類別（例如，在成員函式主體中定義的類別）不會繼承封閉式範圍的**code_seg**屬性。

當**code_seg**屬性套用至樣板類別或範本函式時，會將範本的所有隱含特製化放在指定的區段中。 明確或部分特製化並不會繼承主要範本中的**code_seg**屬性。 您可以在特製化上指定相同或不同的**code_seg**屬性。 **Code_seg**屬性無法套用至明確的範本具現化。

根據預設，編譯器產生的程式碼 (如特殊成員函式) 會在 .text 區段中。 `#pragma code_seg` 指示詞不會覆寫這個預設值。 使用 [類別]、[類別樣板] 或 [函式] 範本上的 [ **code_seg** ] 屬性，即可控制編譯器產生之程式碼的放置位置。

Lambda 會從其封閉範圍繼承**code_seg**屬性。 若要指定 lambda 的區段，請將**code_seg**屬性套用在參數宣告子句之後，以及任何可變動或例外狀況規格、任何尾端傳回類型規格和 lambda 主體之前。 如需詳細資訊，請參閱[Lambda 運算式語法](../cpp/lambda-expression-syntax.md)。 這個範例會在名為 PagedMem 的區段中定義 Lambda：

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

當您將特定成員函式 (尤其是虛擬成員函式) 放在不同的區段時，請特別小心。 若基底類別方法位於非分頁區段，而您在位於分頁區段之衍生類別中定義虛擬函式，其他基底類別方法或使用者程式碼可能會假設叫用該虛擬方法不會觸發分頁錯誤。

## <a name="example"></a>範例

這個範例示範當使用隱含和明確樣板特製化時， **code_seg**屬性如何控制區段位置：

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
