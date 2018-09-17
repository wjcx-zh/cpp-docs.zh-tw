---
title: 推斷規則的優先順序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4f2e7ff55e935b7e425b552ba85f47f134c6b80
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725227"
---
# <a name="precedence-in-inference-rules"></a>推斷規則的優先順序

如果有多重定義推斷規則，NMAKE 就會使用最高優先順序的定義。 下列清單顯示優先順序從最高到低排列的順序：

1. Makefile; 中定義推斷規則更新的定義，其優先順序。

1. Tools.ini; 中定義推斷規則更新的定義，其優先順序。

1. 預先定義的推斷規則。

## <a name="see-also"></a>另請參閱

[推斷規則](../build/inference-rules.md)