---
title: NMAKE 警告 U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: d59b5656d76025fa56bfc76bad800659f25acf53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193195"
---
# <a name="nmake-warning-u4004"></a>NMAKE 警告 U4004

目標 ' targetname ' 的規則太多

使用單一冒號（ **：** ）做為分隔符號，指定了一個以上的描述區塊給給定的目標。 NMAKE 執行了第一個描述區塊中的命令，並忽略稍後的區塊。

若要在多個相依性中指定相同的目標，請使用雙冒號（`::`）做為每個相依性行中的分隔符號。
