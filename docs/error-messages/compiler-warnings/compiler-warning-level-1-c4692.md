---
title: 編譯器警告 (層級 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: d013990d0d56c028f48928d1b48c2e0a66b393af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555831"
---
# <a name="compiler-warning-level-1-c4692"></a>編譯器警告 (層級 1) C4692

'function': 非私用成員的簽章含有組件私用原生類型 'native_type'

組件外部可見的型別包含其簽章包含原生類型不是組件外部可見的成員函式。 因此，如果其包含的型別會具現化組件外，應該不呼叫此成員函式。

如需詳細資訊，請參閱 <<c0> [ 輸入可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>範例

下列範例會產生 C4692。

```
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```