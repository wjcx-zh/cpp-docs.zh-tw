---
title: NMAKE 嚴重錯誤 U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: bfc42c458c1932287f17f367d09c4b23c2c201a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182821"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 嚴重錯誤 U1064

找不到 MAKEFILE，且未指定任何目標

NMAKE 命令列未指定 makefile 或目標，而且目前目錄未包含名為 MAKEFILE 的檔案。

NMAKE 需要 makefile 或命令列目標（或兩者皆是）。 若要讓一個 makefile 可供 NMAKE 使用，請指定/F 選項，或將名為 MAKEFILE 的檔案放在目前的目錄中。 如果未提供 makefile，則 NMAKE 可以使用推斷規則來建立命令列目標。
