---
title: 如何：存取 System::String 中的字元
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: cb62eb0fecbee202e4d01635a60da565241822ee
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686791"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>如何：存取 System::String 中的字元

您可以存取物件的字元，以對 <xref:System.String> 採用字串的非受控函式進行高效能呼叫 `wchar_t*` 。 方法會產生物件之第一個字元的內部指標 <xref:System.String> 。 此指標可以直接操作或釘選，並傳遞至預期一般字串的函式 **`wchar_t`** 。

## <a name="examples"></a>範例

`PtrToStringChars` 傳回 <xref:System.Char> ，也就是內部指標 (也稱為 `byref`) 。 因此，它會受限於垃圾收集。 除非您要將它傳遞給原生函式，否則您不需要釘選此指標。

請考慮下列程式碼：  因為是內部指標，所以不需要釘選， `ppchar` 而且如果垃圾收集行程移動它所指向的字串，它也會更新 `ppchar` 。 若沒有 [pin_ptr (c + +/cli) ](../extensions/pin-ptr-cpp-cli.md)，程式碼將可運作，而且不會因為釘選而造成潛在的效能衝擊。

如果您傳遞 `ppchar` 至原生函式，則它必須是釘選指標; 垃圾收集行程將無法更新非受控堆疊框架上的任何指標。

```cpp
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

此範例顯示需要釘選的位置。

```cpp
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

內部指標具有原生 c + + 指標的所有屬性。 例如，您可以使用它來引導連結的資料結構，並只使用一個指標進行插入和刪除：

```cpp
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>另請參閱

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
