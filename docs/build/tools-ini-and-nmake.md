---
title: Tools.ini 和 NMAKE |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84406886c9aa0c0053ed7c183912bf8a7f1f4771
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723576"
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

NMAKE 讀取 Tools.ini 之前它會讀取 makefile，除非使用 /R。 它會尋找 Tools.ini 第一次在目前的目錄，然後在初始化環境變數所指定的目錄中。 NMAKE 中的設定的初始設定檔案的區段開頭`[NMAKE]`，而且可以包含任何 makefile 的資訊。 指定的註解上以不同的行開頭的數字符號 （#）。

## <a name="see-also"></a>另請參閱

[執行 NMAKE](../build/running-nmake.md)