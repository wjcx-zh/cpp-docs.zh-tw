---
title: NMAKE 警告 U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298148"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004

太多規則目標 'targetname'

指定的目標，使用單一的冒號指定了多個描述區塊 (**:**) 做為分隔符號。 NMAKE 中的第一個描述區塊中執行命令，並忽略更新版本的區塊。

若要在多個相依性中指定相同的目標，使用雙冒號 (`::`) 為每個相依性行分隔符號。