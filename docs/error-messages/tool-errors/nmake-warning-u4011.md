---
title: NMAKE 警告 U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193143"
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011

' target '：並非所有可用的相依性;目標未建立

給定目標的相依可能不存在或已過期，而且用於更新相依的命令傳回非零結束代碼。 /K 選項會告知 NMAKE 繼續處理組建的不相關部分，並在 NMAKE 會話完成時發出結束代碼1。

這個警告前面會加上每個無法建立或更新之相依性的警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) 。
