---
title: NMAKE 警告 U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: f68da1893eec6325ccccfd0e2e2dd0e612f28eb9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193130"
---
# <a name="nmake-warning-u4010"></a>NMAKE 警告 U4010

' target '：組建失敗;已指定/k，正在繼續 。

在命令區塊中，指定目標的命令傳回非零的結束代碼。 /K 選項會告知 NMAKE 繼續處理組建的不相關部分，並在 NMAKE 會話完成時發出結束代碼1。

如果指定的目標為，本身就是另一個目標的相依性，則 NMAKE 會在此警告之後發出警告[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) 。
