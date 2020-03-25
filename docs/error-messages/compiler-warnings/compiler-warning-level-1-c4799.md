---
title: 編譯器警告 (層級 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: ec92da425718cd5ddc579d1d733a0bc4e56dc04a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175099"
---
# <a name="compiler-warning-level-1-c4799"></a>編譯器警告 (層級 1) C4799

> 函式 '*function*' 結尾沒有任何 emm

函式至少有一個 MMX 指令，但沒有 `EMMS` 指令。 使用多媒體指令時，您也應該使用 `EMMS` 指令或 `_mm_empty` 內建來清除 MMX 程式碼結尾的多媒體標記單字。

使用 ivec 時，您可能會收到 C4799，表示程式碼在傳回之前，不會正確地執行 EMM 指令。 對於這些標頭，這是錯誤的警告。 您可以藉由在 IVEC 中定義 _SILENCE_IVEC_C4799 來關閉這些功能。 不過，請注意，這也會讓編譯器不會提供此類型的正確警告。

如需相關資訊，請參閱[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。
