---
title: 巨集定義的優先順序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a3d8873fd1fee61afec865181bab27305bebfd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722211"
---
# <a name="precedence-in-macro-definitions"></a>巨集定義的優先順序

如果巨集有多個定義，NMAKE 就會使用最高優先順序的定義。 下列清單顯示的優先順序，從最高到最低：

1. 在命令列上定義的巨集

1. Makefile 中定義的巨集，或包含檔案

1. 繼承的環境變數巨集

1. Tools.ini 檔案中定義的巨集

1. 預先定義的巨集，例如[CC](../build/command-macros-and-options-macros.md)和[AS](../build/command-macros-and-options-macros.md)

您可以使用 /E，讓繼承自環境變數，以覆寫具有相同名稱的 makefile 巨集的巨集。 使用 **！UNDEF**覆寫命令列。

## <a name="see-also"></a>另請參閱

[定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)