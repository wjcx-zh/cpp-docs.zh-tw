---
title: 推斷規則的優先順序
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
ms.openlocfilehash: ca24134fd1829ad3d97ca67b8c30aae3af4109ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319677"
---
# <a name="precedence-in-inference-rules"></a>推斷規則的優先順序

如果有多重定義推斷規則，NMAKE 就會使用最高優先順序的定義。 下列清單顯示優先順序從最高到低排列的順序：

1. Makefile; 中定義推斷規則更新的定義，其優先順序。

1. Tools.ini; 中定義推斷規則更新的定義，其優先順序。

1. 預先定義的推斷規則。

## <a name="see-also"></a>另請參閱

[推斷規則](inference-rules.md)
