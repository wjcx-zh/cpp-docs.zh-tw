---
title: 在內嵌組譯碼中呼叫 C++ 函式
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 781b60c8973593039c0fdfa2f457170e95048597
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192531"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在內嵌組譯碼中呼叫 C++ 函式

**Microsoft 特定的**

**`__asm`** 區塊只能呼叫未多載的全域 c + + 函式。 如果您呼叫多載的全域 C++ 函式或 C ++ 成員函式，編譯器會發出錯誤。

您也可以呼叫任何以**extern "C"** 連結宣告的函式。 這可讓 **`__asm`** c + + 程式內的區塊呼叫 c 程式庫函式，因為所有標準標頭檔都會宣告程式庫函式具有**Extern "C"** 連結。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內嵌組譯工具](../../assembler/inline/inline-assembler.md)<br/>
