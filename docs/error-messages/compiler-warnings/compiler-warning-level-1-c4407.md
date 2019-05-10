---
title: 編譯器警告 (層級 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 2e47e293b650f64d2a6be91a837cc4195e073e8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447753"
---
# <a name="compiler-warning-level-1-c4407"></a>編譯器警告 (層級 1) C4407

不同成員指標表示法之間進行轉換，編譯器可能會產生不正確的程式碼

偵測到不正確的轉換。

由於編譯器一致性工作，在 Visual Studio 2005 中已完成，就可以產生 C4407。 成員指標現在需要限定的名稱和傳址運算子 (&)。

如果您多個繼承的成員指標至單一繼承的成員指標之間的轉換，可能會發生 C4407。 有時候這可以運作，但有時卻無法因為單一繼承的成員指標表示法不保留足夠的資訊。 在以編譯 **/vmm**有助於 (如需詳細資訊，請參閱[/vmm、 /vms、 /vmv （一般用途表示）](../../build/reference/vmm-vms-vmv-general-purpose-representation.md))。 您也可以嘗試重新排列您的基底類別;編譯器會在轉換中偵測資訊遺失，因為基底類別是從衍生的非零位移。

下列範例會產生 C4407:

```
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