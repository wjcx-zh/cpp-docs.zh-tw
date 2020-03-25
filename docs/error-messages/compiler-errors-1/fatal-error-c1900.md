---
title: 嚴重錯誤 C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202836"
---
# <a name="fatal-error-c1900"></a>嚴重錯誤 C1900

> '*Tool1*' 版本 '*數位 1*' 和 '*tool2*' 版本 '*數位*' 之間的 Il 不符

在編譯器的不同階段中執行的工具不符。 *數位 1*和*數位 2*指的是檔案上的日期。 例如，在階段 1，編譯器前端執行 (c1.dll)，而在階段 2 中，編譯器後端執行 (c2.dll)。 檔案上的日期必須相符。

若要修正這個問題，請確定所有的更新都已套用到 Visual Studio。 如果問題持續發生，請使用 Windows [控制台] 中的 [**程式和功能**] 來修復或重新安裝 Visual Studio。
