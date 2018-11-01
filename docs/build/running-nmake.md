---
title: 執行 NMAKE
ms.date: 09/05/2018
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: 81f38792893955b476dfc7eda91ed00603924a8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646208"
---
# <a name="running-nmake"></a>執行 NMAKE

## <a name="syntax"></a>語法

> **NMAKE** [*選項*...][*巨集*...][*目標*...][**\@**<em>commandfile&lt</em> ...]

## <a name="remarks"></a>備註

只有指定的 NMAKE 組建*目標*或，如果未指定，第一個目標的 makefile 中。 第一次的 makefile 目標可以是[虛擬目標](../build/pseudotargets.md)建置的其他目標。 NMAKE 使用 /F; 使用指定的 makefile如果未指定 /F，它會使用目前的目錄中的 Makefile 檔案。 如果未不指定任何 makefile，建置命令列使用推斷規則*目標*。

*Commandfile&lt*文字檔案 （或回應檔） 包含命令列輸入。 其他輸入可以前面或後面\@ *commandfile&lt*。 允許的路徑。 在  *commandfile&lt*，換行符號會被視為空格。 巨集定義以引號括住包含空格。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[NMAKE 選項](../build/nmake-options.md)

[Tools.ini 和 NMAKE](../build/tools-ini-and-nmake.md)

[NMAKE 的結束代碼](../build/exit-codes-from-nmake.md)

## <a name="see-also"></a>另請參閱

[NMAKE 參考](../build/nmake-reference.md)