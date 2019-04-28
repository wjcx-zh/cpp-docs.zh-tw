---
title: NMAKE 警告 U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 3b73e92c929b3dd5924584ab732f731d565d0430
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359770"
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011

'target': 不是所有的相依性，可使用;未建置目標

指定目標的相依性不存在或已過期，並更新相依的命令傳回非零的結束代碼。 [/K] 選項會告訴 NMAKE 繼續處理組建的不相關的部分，並發出結束代碼為 1，當 NMAKE 工作階段完成時。

這個警告會加上警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md)用於無法建立或更新每個相依。