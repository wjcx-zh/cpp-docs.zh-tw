---
title: 1.4 合規性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a332d8fb5de172c363c6f9c1bebba65d6fa0ff8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381812"
---
# <a name="14-compliance"></a>1.4 符合標準

實作的 OpenMP C/c + + API *OpenMP 相容*如果它會辨識並章節 1、 2、 3、 4 中所保留的所有項目，此規格，語意和附錄 c 附錄 A、 B、 D、 E 和 F 的資訊之用，而且不規格的一部分。 包含的 API 子集的實作不 OpenMP 標準。

OpenMP C 和 c + + API 會受到所實作的基底語言擴充功能。 如果基底的語言不支援的語言建構或延伸模組，會出現在這份文件中，OpenMP 實作不是需要支援它。

所有標準 C 和 c + + 程式庫函式和內建函式 （也就是函式的編譯器有特定的知識） 必須是安全執行緒。 未同步處理的使用由不同的執行緒在平行區域內的安全執行緒的函式不會產生未定義的行為。 不過，行為可能不會如所示的序列的區域相同。 （數字產生隨機的函式是舉例）。

OpenMP C/c + + API 可讓您指定特定的行為是*實作定義。* 若要定義並記錄其行為在這些情況下需要合格的 OpenMP 實作。 請參閱[附錄 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)，頁面 97，如需實作定義行為的清單。