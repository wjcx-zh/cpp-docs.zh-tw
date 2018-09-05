---
title: 在內嵌組譯碼中呼叫 c + + 函式 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4717ae24dc1a0b6f51f7a00f68f6569c2f988c65
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678940"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在內嵌組譯碼中呼叫 C++ 函式

**Microsoft 專屬**

`__asm` 區塊只能呼叫未多載的全域 C++ 函式。 如果您呼叫多載的全域 C++ 函式或 C ++ 成員函式，編譯器會發出錯誤。

您也可以呼叫宣告的任何函式**extern"C"** 連結。 這可讓`__asm`區塊中呼叫 C 程式庫函式，因為所有標準標頭檔宣告具有程式庫函式的 c + + 程式**extern"C"** 連結。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>