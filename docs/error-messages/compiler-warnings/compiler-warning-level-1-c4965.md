---
title: 編譯器警告 (層級 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: e882cabdf38fd9bc926fbaa04352ba9d0ace90ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174410"
---
# <a name="compiler-warning-level-1-c4965"></a>編譯器警告 (層級 1) C4965

整數0的隱含方塊;使用 nullptr 或明確轉換

視覺C++特徵：實數值型別的隱含裝箱。 使用 Managed 延伸模組產生 null 指派的C++指令，現在會成為對已裝箱 int 的指派。

如需詳細資訊，請參閱 [Boxing](../../extensions/boxing-cpp-component-extensions.md)中定義的介面的私用 C++ 專屬實作。

## <a name="example"></a>範例

下列範例會產生 C4965。

```cpp
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```
