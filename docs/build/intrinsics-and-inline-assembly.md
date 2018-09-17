---
title: 內建函式和內嵌組譯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a87e577af339099eda56a3b9d91929a05253a43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716244"
---
# <a name="intrinsics-and-inline-assembly"></a>內建和內嵌組譯

其中一個條件約束，適用於 x64 編譯器會為沒有內嵌組譯工具支援。 函式，這表示無法寫入 C 或 c + + 中是必須可寫入為副程式或編譯器所支援的內建函式。 某些函式是效能敏感，而有些則不。 重視效能的函式應該實作為內建函式。

編譯器所支援的內建函式中所述[編譯器內建](../intrinsics/compiler-intrinsics.md)。

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)