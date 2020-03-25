---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 920135943c9dfb46b00ee6ceb2535fde128dffb0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172031"
---
# <a name="pin_ptr-ccli"></a>pin_ptr (C++/CLI)

可需告只和 Common Language Runtime 搭配使用的「Pin 指標」。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

## <a name="windows-runtime"></a>Windows 執行階段

(Windows 執行階段不支援這個語言功能。)

## <a name="common-language-runtime"></a>Common Language Runtime

「Pin 指標」是一個內部指標，可防止指向的物件在記憶體回收堆積上移動。 也就是 Common Language Runtime 不會變更 Pin 指標的值。 利用這種方式將受控類別的位址傳遞至非受控函式是必要的，可讓位址不會在解析非受控函式呼叫時意外變更。

### <a name="syntax"></a>語法

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>參數

*cv_qualifier*<br/>
**const** 或 **volatile** 限定詞。 根據預設，Pin 指標是 **volatile**。 宣告 Pin 指標 **volatile** 是多餘的，但不是錯誤。

*type*<br/>
*initializer* 的型別。

*var*<br/>
**pin_ptr** 變數的名稱。

*initializer*<br/>
參考類型的成員，Managed 陣列的元素，或是其他任何可以指派至原生指標的物件。

### <a name="remarks"></a>備註

**pin_ptr** 代表原生指標功能的超集。 因此，只要是可以指派至原生指標的任何物件，也都可以指派至 **pin_ptr**。 內部指標可以執行與原生指標相同的一組作業，包括比較和指標算術。

您可以固定受控類別的物件和子物件，防止 Common Language Runtime 在記憶體回收期間移動它們。 這個做法的主要用途是將指標作為非受控函式呼叫的實際參數，傳遞至受控資料。 在收集週期期間，執行階段會檢查為 Pin 指標建立的中繼資料，而且不會移動它所指向的項目。

固定物件時也會固定它的值欄位；也就是基本類型或值類型的欄位。 不過，透過追蹤控制代碼宣告的欄位 (`%`) 不會固定。

固定受控物件中定義的子物件具有固定整個物件的效果。

如果重新指派 Pin 指標以指向新值，之前指定的執行個體就不再視為已固定。

只有在 **pin_ptr** 指向物件時才能將它固定。 當物件的 Pin 指標超出範圍或設為 [nullptr](nullptr-cpp-component-extensions.md) 時，就不會再將它視為已固定。 在 **pin_ptr** 超出範圍後，之前固定的物件就可以透過記憶體回收行程在堆積中移動。 仍指向該物件的任何原生指標將不會更新，而且對它們其中之一進行取值 (Dereference)，可能會引發無法復原的例外狀況。

如果沒有 Pin 指標指向物件 (因為所有 Pin 指標皆超出範圍、已重新指派以指向其他物件，或已設為 [nullptr](nullptr-cpp-component-extensions.md))，表示物件一定沒有固定。

Pin 指標可以指向參考控制代碼、實值型別或 Boxed 類型控制代碼、受控型別的成員，或是指向受控陣列的元素。 它無法指向參考型別。

如果 **pin_ptr** 指向原生物件，採用其位址會導致出現未定義的行為。

Pin 指標在堆疊中只能宣告為非靜態區域變數。

Pin 指標不可做為下列項目使用：

- 函式參數

- 函式的傳回型別

- 類別的成員

- 轉換的目標型別。

**pin_ptr** 位於 `cli` 命名空間之中。 如需詳細資訊，請參閱[平台、預設與 cli 命名空間](platform-default-and-cli-namespaces-cpp-component-extensions.md)。

如需內部指標的詳細資訊，請參閱 [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)。

如需釘選指標的詳細資訊，請參閱[如何：釘選指標和陣列](how-to-pin-pointers-and-arrays.md)和[如何：宣告固定指標和實數值型別](how-to-declare-pinning-pointers-and-value-types.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

以下範例會使用 **pin_ptr** 限制陣列第一個元素的位置。

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

以下範例會示範內部指標可轉換成 Pin 指標，以及當運算元位於受控堆積上時，運算子位址的傳回類型 (`&`) 會是一個內部指標。

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

以下範例會示範將 Pin 指標轉換成其他型別。

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
