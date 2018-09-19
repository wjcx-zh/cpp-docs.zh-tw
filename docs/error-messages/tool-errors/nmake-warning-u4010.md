---
title: NMAKE 警告 U4010 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a640245db460f4cd8cd658c097955a69a59d1fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117489"
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010

'target': 建置失敗;/K 指定，繼續...

指定之目標的命令區塊中的命令傳回非零結束代碼。 [/K] 選項會告訴 NMAKE 繼續處理組建的不相關的部分，並發出結束代碼為 1，當 NMAKE 工作階段完成時。

如果指定的目標，本身，另一個目標相依，NMAKE 就會發出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)後這項警告。