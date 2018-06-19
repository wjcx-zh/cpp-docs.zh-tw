---
title: 巨集定義的優先順序 |Microsoft 文件
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
ms.openlocfilehash: 6ce6f0acc898dc719d2252d5cc59dff92bda4a98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368609"
---
# <a name="precedence-in-macro-definitions"></a>巨集定義的優先順序
如果巨集有多個定義，NMAKE 就會使用最高優先順序的定義。 下列清單顯示的優先順序，從最高到最低：  
  
1.  在命令列上所定義的巨集  
  
2.  Makefile 中定義的巨集，或包含檔案  
  
3.  繼承的環境變數巨集  
  
4.  Tools.ini 檔案中定義的巨集  
  
5.  預先定義的巨集，例如[CC](../build/command-macros-and-options-macros.md)和[AS](../build/command-macros-and-options-macros.md)  
  
 您可以使用 /E，讓繼承自環境變數，以覆寫具有相同名稱的 makefile 巨集的巨集。 使用 **！UNDEF**覆寫命令列。  
  
## <a name="see-also"></a>另請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)