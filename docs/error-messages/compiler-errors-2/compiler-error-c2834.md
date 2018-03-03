---
title: "編譯器錯誤 C2834 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 616bb6fe351c7575bf04f319390d0a3cfcd3cc8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2834"></a>編譯器錯誤 C2834
'operator operator' 必須全域限定  
  
 `new`和`delete`運算子會繫結至類別所在的位置。 無法選取的版本使用範圍解析`new`或`delete`自其他類別。 若要實作的多種形式`new`或`delete`運算子，使用額外的型式參數建立運算子版本。