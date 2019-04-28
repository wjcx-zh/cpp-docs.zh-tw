---
title: NMAKE 警告 U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: aa4d2355b18a3c6cc6fc3151c7662fbbbaa665d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298109"
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010

'target': 建置失敗;/K 指定，繼續...

指定之目標的命令區塊中的命令傳回非零結束代碼。 [/K] 選項會告訴 NMAKE 繼續處理組建的不相關的部分，並發出結束代碼為 1，當 NMAKE 工作階段完成時。

如果指定的目標，本身，另一個目標相依，NMAKE 就會發出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)後這項警告。