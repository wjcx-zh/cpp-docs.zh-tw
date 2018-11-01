---
title: 如何：宣告及使用內部指標和 Managed 陣列 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
ms.openlocfilehash: 98f198812654706792ea18024bb8654803d27970
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598259"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>如何：宣告及使用內部指標和 Managed 陣列 (C++/CLI)

下列 C + + /cli CLI 範例會示範如何宣告和使用內部指標陣列。

> [!IMPORTANT]
> `/clr` 編譯器選項支援這項語言功能，`/ZW` 編譯器選項則不支援。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```cpp
// interior_ptr_arrays.cpp
// compile with: /clr
#define SIZE 10

int main() {
   // declare the array
   array<int>^ arr = gcnew array<int>(SIZE);

   // initialize the array
   for (int i = 0 ; i < SIZE ; i++)
      arr[i] = i + 1;

   // create an interior pointer into the array
   interior_ptr<int> ipi = &arr[0];

   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);

   ipi++;
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);
}
```

```Output
1st element in arr holds: 1
ipi points to memory address whose value is: 1
after incrementing ipi, it points to memory address whose value is: 2
```

## <a name="see-also"></a>另請參閱

[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)