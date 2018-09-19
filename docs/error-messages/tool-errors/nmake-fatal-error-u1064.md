---
title: NMAKE 嚴重錯誤 U1064 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4240bf2c553957e73d5ead0bdd03ea129450645b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092995"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 嚴重錯誤 U1064

找不到 MAKEFILE，且沒有指定目標

NMAKE 命令列中未指定以 makefile 或目標，且目前的目錄未包含名為 MAKEFILE 的檔案。

NMAKE 需要 makefile 框線或命令列目標 （或兩者都有）。 若要可讓 NMAKE makefile 使用，指定 [/F] 選項，或是將目前的目錄中名為 MAKEFILE 檔案。 NMAKE 可以使用推斷規則，如果未提供的 makefile，以建立命令列的目標。