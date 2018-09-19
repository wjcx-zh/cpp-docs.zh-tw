---
title: NMAKE 警告 U4004 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a89bb8abf212c8a0ffa9fb40fe5d3ea43307a08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016646"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004

太多規則目標 'targetname'

指定的目標，使用單一的冒號指定了多個描述區塊 (**:**) 做為分隔符號。 NMAKE 中的第一個描述區塊中執行命令，並忽略更新版本的區塊。

若要在多個相依性中指定相同的目標，使用雙冒號 (`::`) 為每個相依性行分隔符號。