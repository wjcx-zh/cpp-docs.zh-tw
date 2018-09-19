---
title: 編譯器錯誤 C2818 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f692f52477c988c277f60a689dac5ce83a90acb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112040"
---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818

多載 'operator ->' 透過類型 'type' 遞迴應用

類別成員存取運算子的重複定義包含遞迴`return`陳述式。 若要重新定義`->`運算子進行遞迴時，您必須移動到個別函式呼叫運算子的遞迴常式覆寫函式。