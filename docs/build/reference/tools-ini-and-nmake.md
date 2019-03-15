---
title: Tools.ini 和 NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 38eebb3aaf07438da85b0cfe6bd3f26fb5d6db29
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824851"
---
# <a name="toolsini-and-nmake"></a>Tools.ini 和 NMAKE

NMAKE 讀取 Tools.ini 之前它會讀取 makefile，除非使用 /R。 它會尋找 Tools.ini 第一次在目前的目錄，然後在初始化環境變數所指定的目錄中。 NMAKE 中的設定的初始設定檔案的區段開頭`[NMAKE]`，而且可以包含任何 makefile 的資訊。 指定的註解上以不同的行開頭的數字符號 （#）。

## <a name="see-also"></a>另請參閱

[執行 NMAKE](running-nmake.md)
