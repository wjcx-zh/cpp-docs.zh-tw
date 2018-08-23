---
title: pin_ptr (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
dev_langs:
- C++
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af0cfe6f3a94aa1bc2afc4e4857864f81099567e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591727"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)

宣告*pin 指標*，這只適用於 common language runtime。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

（這個語言功能不支援在 Windows 執行階段）。

## <a name="common-language-runtime"></a>Common Language Runtime

A *pin 指標*可防止物件的內部指標指向的記憶體回收堆積上移動。 也就是 common language runtime 不會變更 pin 指標的值。 當您必須將 managed 類別的位址傳遞 unmanaged 函式讓位址將不會意外地在解析 unmanaged 函式呼叫的期間，這是必要的。

### <a name="syntax"></a>語法

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>參數

*cv_qualifier*  
**const**或是**volatile**限定詞。 根據預設，pin 指標是**volatile**。 它是多餘，但不是錯誤來宣告 pin 指標**volatile**。

*type*  
型別*初始設定式*。

*var*  
名稱**pin_ptr**變數。

*initializer*  
參考類型的成員，Managed 陣列的元素，或是其他任何可以指派至原生指標的物件。

### <a name="remarks"></a>備註

A **pin_ptr**代表原生指標的功能超集。 因此，任何可以指派給原生指標的項目也可指派給**pin_ptr**。 內部指標可以執行與原生指標相同的一組作業，包括比較和指標算術。

物件或 managed 類別的子物件都可以釘選，在此情況下，common language runtime 不會移動它在記憶體回收期間。 主要的用途是將指標傳遞給受管理的資料中，當做 unmanaged 函式呼叫的實質參數。 在集合的週期中，執行階段會檢查為 pin 指標建立的中繼資料，並不會移動它所指向的項目。

釘選物件也會釘選它的值欄位;也就是基本類型的欄位或值類型。 不過，欄位宣告的追蹤控制代碼 (`%`) 不會固定。

釘選 managed 物件中定義的子物件具有釘選整個物件的效果。

如果 pin 指標會指派給新的值所指向，指向先前的執行個體不再被視為釘選。

已釘選的物件，而**pin_ptr**指向它。 其 pin 指標超出範圍，或設為當物件不再釘選[nullptr](../windows/nullptr-cpp-component-extensions.md)。 在後**pin_ptr**可以由記憶體回收行程堆積中移動超出範圍，已釘選的物件。 仍然指向該物件任何原生指標將不會更新，以及取值 (dereference) 其中一個可能會引發例外狀況無法復原。

如果沒有 pin 指標指向的物件 (所有 pin 指標超出範圍發生、 已重新指派給指向其他物件，或已指派[nullptr](../windows/nullptr-cpp-component-extensions.md))，該物件保證不會釘選。

Pin 指標可以指向參考控制代碼、 實值型別或 boxed 的類型控制代碼、 managed 類型的成員或 managed 陣列的項目。 它無法指向參考型別。

位址**pin_ptr**指向原生的物件會導致未定義的行為。

Pin 指標只可以宣告為非靜態區域變數中，但會在堆疊上。

Pin 指標不能做：

- 函式參數

- 函式的傳回類型

- 類別的成員

- 轉換目標型別。

**pin_ptr**處於`cli`命名空間。 如需詳細資訊，請參閱 < [Platform、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

如需有關內部指標的詳細資訊，請參閱[interior_ptr (C + + /cli CLI)](../windows/interior-ptr-cpp-cli.md)。

如需 pin 指標的詳細資訊，請參閱[如何： Pin 指標和陣列](../windows/how-to-pin-pointers-and-arrays.md)並[如何： 宣告 Pin 指標和實值類型](../windows/how-to-declare-pinning-pointers-and-value-types.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例會使用**pin_ptr**限制陣列的第一個元素的位置。

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

下列範例顯示，讓內部指標可以轉換成 pin 的指標，並傳址運算子的傳回類型 (`&`) 是內部指標，如果運算元為 managed 堆積上。

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

下列範例會示範，pin 指標可以轉換成另一種類型。

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```