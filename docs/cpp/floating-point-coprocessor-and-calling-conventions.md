---
title: 浮點常數副處理器和呼叫慣例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46cf9c937453894ed37ad434ad94609d0744be24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮點常數副處理器和呼叫慣例
如果您要為浮點常式點副處理器撰寫組件，您必須保留浮點控制字詞並清除副處理器堆疊，除非您要傳回**float**或**double**值 （其 ST(0)) 應該傳回您的函式。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)