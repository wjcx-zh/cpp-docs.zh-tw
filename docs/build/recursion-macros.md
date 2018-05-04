---
title: 遞迴巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759deaff6014cbba40c97f9d627baf6a800732f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="recursion-macros"></a>遞迴巨集
您可以使用遞迴巨集來呼叫 NMAKE 以遞迴方式。 遞迴工作階段會繼承命令列和環境變數巨集和 Tools.ini 資訊。 不會繼承 makefile 定義推斷規則或**。尾碼**和**。珍貴**規格。 若要傳遞到工作階段遞迴 NMAKE 巨集，設定環境變數設定，遞迴呼叫之前，定義巨集遞迴呼叫，在命令中或 Tools.ini 中定義的巨集。  
  
|巨集|定義|  
|-----------|----------------|  
|**請**|原先用來叫用 NMAKE 命令。<br /><br /> Nmake.exe $(MAKE) 巨集提供的完整路徑。|  
|**MAKEDIR**|NMAKE 叫用時的目前目錄。|  
|**MAKEFLAGS**|目前作用中的選項。 使用做為`/$(MAKEFLAGS)`。  請注意，就不會包含 /F。|  
  
## <a name="see-also"></a>另請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)