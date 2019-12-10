---
title: 編譯器警告 (層級 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: ac97a943e6a8178e930d93a097071b0e3da09773
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989059"
---
# <a name="compiler-warning-level-4-c4820"></a>編譯器警告 (層級 4) C4820

在成員建構 'member_name' 之後加入 'bytes' 位元組填補

專案的類型和順序會導致編譯器在結構的結尾加上填補。 如需有關在結構中填補的詳細資訊，請參閱[align](../../cpp/align-cpp.md) 。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4820：

```cpp
// C4820.cpp
// compile with: /W4 /c
#pragma warning(default : 4820)

// Delete the following 4 lines to resolve.
__declspec(align(2)) struct MyStruct {
   char a;
   int i;   // C4820
};

// OK
#pragma pack(1)
__declspec(align(1)) struct MyStruct2 {
   char a;
   int i;
};
```
