---
title: 編譯器警告 (層級 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: c7a2d72b429f762e476286093c7f273a9a546cb6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174670"
---
# <a name="compiler-warning-level-1-c4917"></a>編譯器警告 (層級 1) C4917

' 宣告子 '： GUID 只能與類別、介面或命名空間產生關聯

[類別](../../cpp/class-cpp.md)、[介面](../../cpp/interface.md)或[命名空間](../../cpp/namespaces-cpp.md)以外的使用者定義結構不能有 GUID。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

## <a name="example"></a>範例

下列程式碼範例會產生 C4917：

```cpp
// C4917.cpp
// compile with: /W1
#pragma warning(default : 4917)
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S
{
} s;   // C4917, don't put uuid on a struct

int main()
{
}
```
