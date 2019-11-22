---
title: 遞迴巨集
description: 描述您用來在遞迴會話中呼叫 NMAKE 的宏。
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303150"
---
# <a name="recursion-macros"></a>遞迴巨集

使用遞迴宏以遞迴方式呼叫 NMAKE。 遞迴會話會繼承命令列和環境變數宏和工具 .ini 資訊。 它們不會繼承 makefile 定義的推斷規則，也不會 `.SUFFIXES` 和 `.PRECIOUS` 規格。 有三種方式可將宏傳遞至遞迴的 NMAKE 會話：在遞迴呼叫之前，使用 :::no-loc text="SET"::: 命令來設定環境變數。 在命令中定義遞迴呼叫的宏。 或者，在 Tools .ini 中定義宏。

|巨集|定義|
|-----------|----------------|
|**MAKE**|原先用來叫用 NMAKE 的命令。<br /><br /> `$(MAKE)` 宏會提供 nmake 的完整路徑。|
|**MAKEDIR**|叫用 NMAKE 時的目前的目錄。|
|**MAKEFLAGS**|目前作用中的選項。 使用做為 `/$(MAKEFLAGS)`。 不包含 **/f**選項。|

## <a name="see-also"></a>請參閱

[特殊的 NMAKE 宏](special-nmake-macros.md)
