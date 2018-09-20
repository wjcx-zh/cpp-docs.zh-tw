---
title: 初始設定式清單 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 981f2737d370dc25ca4e7dc6c20947b3867a0c65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394604"
---
# <a name="initializer-lists"></a>初始設定式清單

建構函式中的初始設定式清單現在會呼叫基底類別建構函式之前。

## <a name="remarks"></a>備註

在 Visual c + + 2005年之前已在初始設定式清單之前呼叫的基底類別建構函式 Managed Extensions for c + + 進行編譯時。 現在，進行編譯時 **/clr**，會先呼叫初始設定式清單。

## <a name="see-also"></a>另請參閱

[一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)