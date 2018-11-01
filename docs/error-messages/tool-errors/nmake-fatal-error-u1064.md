---
title: NMAKE 嚴重錯誤 U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463358"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 嚴重錯誤 U1064

找不到 MAKEFILE，且沒有指定目標

NMAKE 命令列中未指定以 makefile 或目標，且目前的目錄未包含名為 MAKEFILE 的檔案。

NMAKE 需要 makefile 框線或命令列目標 （或兩者都有）。 若要可讓 NMAKE makefile 使用，指定 [/F] 選項，或是將目前的目錄中名為 MAKEFILE 檔案。 NMAKE 可以使用推斷規則，如果未提供的 makefile，以建立命令列的目標。