---
title: 編譯器錯誤 C2818 |Microsoft 文件
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
ms.openlocfilehash: 10d7f419d528fcd2445b82e29d92442002624909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236049"
---
# <a name="compiler-error-c2818"></a>編譯器錯誤 C2818
多載 'operator ->' 透過類型 'type' 遞迴應用  
  
 類別成員存取運算子的重新定義包含遞迴`return`陳述式。 若要重新定義`->`運算子遞迴時，您必須移動到個別的函式呼叫運算子的遞迴常式覆寫函式。