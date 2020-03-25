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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169574"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在內嵌組譯碼中呼叫 C++ 函式

**Microsoft 專屬**

`__asm` 區塊只能呼叫未多載的全域 C++ 函式。 如果您呼叫多載的全域 C++ 函式或 C ++ 成員函式，編譯器會發出錯誤。

您也可以呼叫任何以**extern "C"** 連結宣告的函式。 這可讓C++程式內的 `__asm` 區塊呼叫 C 程式庫函式，因為所有標準標頭檔都會宣告程式庫函式具有**extern "C"** 連結。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>
