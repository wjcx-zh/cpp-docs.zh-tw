---
title: 編譯器錯誤 C3646 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3646
dev_langs:
- C++
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c038520c1a35fa5264e1e98b074687efb336d028
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "35658607"
---
# <a name="compiler-error-c3646"></a>編譯器錯誤 C3646

> 'specifier': 未知的覆寫規範

## <a name="remarks"></a>備註

編譯器發現語彙基元，它預期會找到 覆寫規範，但編譯器無法辨識的語彙基元的位置。

例如，如果無法辨識*規範*是 **_NOEXCEPT**，它取代為關鍵字**noexcept**。

如需詳細資訊，請參閱 <<c0> [ 覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3646，並示範如何修正此問題：

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```