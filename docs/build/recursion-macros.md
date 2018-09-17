---
title: 遞迴巨集 |Microsoft Docs
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
ms.openlocfilehash: f91a5f327686a522608b6eec9fd7106cbab00028
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702036"
---
# <a name="recursion-macros"></a>遞迴巨集

您可以使用遞迴巨集來呼叫 NMAKE 以遞迴方式。 遞迴工作階段會繼承命令列和環境變數巨集和 Tools.ini 資訊。 但是不會繼承 makefile 定義推斷規則或 **。尾碼**和 **。寶貴**規格。 若要傳送至遞迴 NMAKE 工作階段的巨集，請使用 SET 設定環境變數的遞迴呼叫之前，定義巨集在命令中，遞迴呼叫，或 Tools.ini 中定義的巨集。

|巨集|定義|
|-----------|----------------|
|**請**|原先用來叫用 NMAKE 命令。<br /><br /> $(MAKE) 巨集可讓 nmake.exe 的完整路徑。|
|**MAKEDIR**|NMAKE 叫用時的目前目錄。|
|**MAKEFLAGS**|目前作用中的選項。 做為`/$(MAKEFLAGS)`。  請注意，就不會包含 /F。|

## <a name="see-also"></a>另請參閱

[特殊的 NMAKE 巨集](../build/special-nmake-macros.md)