---
title: 編譯器警告 (層級 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 8dd78872d4edf82fb61c8ab93639dbcd93085754
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162539"
---
# <a name="compiler-warning-level-1-c4407"></a>編譯器警告 (層級 1) C4407

在成員表示的不同指標之間進行轉換時，編譯器可能會產生不正確的程式碼

偵測到不正確的轉換。

C4407 可以因為在 Visual Studio 2005 中完成的編譯器一致性工作而產生。 成員指標現在需要限定名稱和位址運算子（&）。

如果您將多個繼承成員指標轉換成單一繼承成員，則可能會發生 C4407。 有時候這可以正常執行，但有時無法執行，因為單一繼承成員指標標記法並不會保存足夠的資訊。 使用 **/vmm**進行編譯可能有所説明（如需詳細資訊，請參閱[/vmm、/vms、/Vmv （一般用途標記法）](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)）。 您也可以嘗試重新排列基類;編譯器偵測到轉換中的資訊遺失，因為基類與衍生的非零位移。

下列範例會產生 C4407：

```cpp
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```
