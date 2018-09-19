---
title: NMAKE 警告 U4011 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1038ee86f76789451565ab6799795c851c95a95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118332"
---
# <a name="nmake-warning-u4011"></a>NMAKE 警告 U4011

'target': 不是所有的相依性，可使用;未建置目標

指定目標的相依性不存在或已過期，並更新相依的命令傳回非零的結束代碼。 [/K] 選項會告訴 NMAKE 繼續處理組建的不相關的部分，並發出結束代碼為 1，當 NMAKE 工作階段完成時。

這個警告會加上警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md)用於無法建立或更新每個相依。