---
title: NMAKE 的結束代碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c70c76292b62560b1d9895aca2851b4cf56802b
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861794"
---
# <a name="exit-codes-from-nmake"></a>NMAKE 的結束代碼

NMAKE 會傳回下列結束代碼：

|程式碼|意義|
|----------|-------------|
|0|沒有錯誤 （可能是警告）|
|1|未完成的組建 （只有在使用 /K 時才會發出）|
|2|程式錯誤，可能是因為下列其中之一：|
||-Makefile 中的 a 語法錯誤|
||-來自命令的錯誤或結束程式碼|
||-使用者中斷|
|4|系統錯誤： 記憶體不足|
|255|目標不是最新的 （只有在使用 /Q 時才會發出）|

## <a name="see-also"></a>另請參閱

[執行 NMAKE](../build/running-nmake.md)